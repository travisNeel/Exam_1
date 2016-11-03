
_proc:                                  ## @proc
## BB#0:
	push	rbp
	//Copy data from rbp onto top of stack. 
Ltmp0:
Ltmp1:
	mov	rbp, rsp
	// move the data in rsp to rbp , stack pointer now points to rbp
Ltmp2:
	sub	rsp, 16
	// subtract 16 from rsp (setting aside a 16-bit chunk of memory in stack?)

	lea	rax, [rip + L_.str]
	// loads address plus length of the string into register rax

	mov	dword ptr [rbp - 4], edi
	// point to 32bit value held in edi

	mov	esi, dword ptr [rbp - 4]
	// load data of pointer into register esi

	mov	rdi, rax
	//move data in rax to rdi

	mov	al, 0
	// al = 0

	call	_printf
	// calls the print function

	mov	dword ptr [rbp - 8], eax ## 4-byte Spill
	
	add	rsp, 16
	// add 16 to stack pointer

	pop	rbp
	// removes rbp from stack

	ret
	// return to call location

L_.str:                                 ## @.str
	.asciz	"The parameter vlue was %d\n"



~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


_main:                                  ## @main
## BB#0:
	push	rbp
	// adds rbp to top of stack
Ltmp0:
Ltmp1:
	mov	rbp, rsp
	// moves value held in stack pointer to rbp
	// or changes stack pointer rsp to point to rbp since is newest
Ltmp2:
	sub	rsp, 32
	// subtracts 32 from rsp

	mov	dword ptr [rbp - 4], edi
	
	mov	qword ptr [rbp - 16], rsi

	mov	dword ptr [rbp - 20], 42

	mov	edi, dword ptr [rbp - 20]

	call	_proc
	// calls the _proc program

	xor	eax, eax
	// true if only one eax is true

	add	rsp, 32
	// adds 32 to rsp

	pop	rbp
	//removes rbp from stack

	ret
	//returns to call location



