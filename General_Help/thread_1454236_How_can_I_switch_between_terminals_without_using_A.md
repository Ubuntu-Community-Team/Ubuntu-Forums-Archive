---
title: "How can I switch between terminals without using Alt + Ctrl + F&lt;num&gt; keys?"
date: 2010-04-14
forum: General Help
---

### Post by kumaraSrlk on 2010-04-14
Hi guys,

This is it. Alt + Ctrl + F key won't work for me!.

I run kubuntu 9.10 on vmWare and what i want to do is to switch between virtual terminals. I tried Alt + Ctrl + F key combination and it only work once!, say for example, i'm working in GUI on terminal 7(tty7) and i press Alt + Ctrl + F1 to go to tty1. It takes me to tty1 and i can log in, then i come back to GUI using Alt + Ctrl + F7, but after that Alt + Ctrl + F1 doesn't take me back to tty1, no matter how much i try.
What i can do is to press Alt + Ctrl + F2 and goto tty2 and without logging in, press Alt + Ctrl + F1 to goto tty1. And again, this won't work for a second time!!. This keeps happening to all the other terminals.

So pls tell me, is there a command to switch between terminals??

Thanks.

---

### Post by kumaraSrlk on 2010-04-14
OK i got the solution myself. This problem is due to vmWare itself. Alt + Ctrl key combination has a special meaning to vmWare thought, i don't know why it worked at least once.

The solution is to use Alt + Ctrl + Shift + F<num of terminal> to switch.More info at [http://www.novell.com/coolsolutions/feature/15955.html#TIP:_Switching_Between_Virtual_Consoles]("http://www.novell.com/coolsolutions/feature/15955.html#TIP:_Switching_Between_Virtual_Consoles")

---

