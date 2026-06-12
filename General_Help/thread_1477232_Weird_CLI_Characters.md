---
title: "Weird CLI Characters"
date: 2010-05-08
forum: General Help
---

### Post by basketballler77 on 2010-05-08
I currently have a problem with the characters in my CLI on tty1. While b,c,d,e,i,o,p,r and s are displayed normally (only discussing lowercase letters currently), and all of the rest are other characters. For example, f is the degree symbol, g is the plus/minus symbol, y is less than or equal to and z is greater than or equal to. 

Prior to this problem occurring I had run a program which ran into a Segmentation Fault. I ignored it, and then, just out of curiosity, used cat to look at the machine code in the program that caused this. At that moment most of the alphabet was replaced. Now every character printed to that terminal is effectively translated, including the prompt. I have logged out and back in and switched shells and the problem persists. 

I've tried other programs. Everything still works, including installing programs. It's just kinda difficult to read. I think it'd be cool to have something set up where this happens when I want to, but I don't want to have to decipher this stuff all the time. Anybody know why this might be happening?

Thanks,
~Jack

---

