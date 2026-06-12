---
title: "return value for shell"
date: 2010-09-01
forum: General Help
---

### Post by abhishek.biradar on 2010-09-01
check the following program
/*a.c*/
int main()
{
         return 0;
}
returns 0 to the shell and echo $? gives 0
/*b.c*/
void main()
{
}
echo $? in shell gives some different values for each execution what does it represents????

---

### Post by Brandon Williams on 2010-09-01
The C spec states "If the return type [of main] is not compatible with int, the termination status returned to the host environment is unspecified." What this means is that you can only rely on the termination status if main has a return type that can be converted to int. This is why the compiler will warn when the return type of main is not int and you compile with -Wall.

Additionally, it's important to note that on a POSIX system, only 7-bit numbers (0-127) are meaningful return values / exit codes, because numbers greater from 128-255 have a special meaning in the shell and there is no way to return an exit status greater than 255 from a program.

In short, always return int from main and always ensure that your return/exit code is between 0 and 127.

---

