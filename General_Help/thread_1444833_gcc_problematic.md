---
title: "gcc problematic?"
date: 2010-04-01
forum: General Help
---

### Post by haopengcu on 2010-04-01
I am using Ubuntu 8.04 and I tried to compile the following simple C code about FILE IO.

#include<stdio.h>

int main(void){
  FILE * fp;
  fp=fopen("trial.txt","w");

  fprintf(fp,"%1.8f\n",3.2);
  fclose(fp);

  return 0;
}

I tried to compile with gcc, how it failed with the following error message.

/tmp/ccSoFk87.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0' collect2: ld returned 1 exit status

However, if I use g++ to compile instead, it works fine.

What is wrong with my gcc?

Thanks

---

### Post by gmargo on 2010-04-01
Works fine for me on 8.04 Hardy.  Do you have the **build-essential** package installed?  Are you fully up-to-date?  Have you been merrily compiling & installing things that overwrite standard tools or libraries?

---

### Post by falconindy on 2010-04-01
What's the file extension you're using? Case matters -- .C is not the same as .c (and .C will be considered to be c++).

---

### Post by marioandres on 2010-04-01
can you show us the command used for compile?
thanks

---

### Post by haopengcu on 2010-04-01
> **falconindy said:**
> What's the file extension you're using? Case matters -- .C is not the same as .c (and .C will be considered to be c++).
I simply used "gcc filename".

You are right. I should change .C to .c. The capital case is not for gcc.

Thanks a lot.

---

