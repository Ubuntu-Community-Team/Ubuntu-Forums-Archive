---
title: "Help with script files!!!"
date: 2010-02-04
forum: General Help
---

### Post by hakermania on 2010-02-04
Hi all! I hope I am posting to the right section...
I am currently working on a program in C with QtCreator.
What I want to do is not only to call a system's .sh file, but edit the .sh file in a way that the user have the opportunity after running it to set his on variables.
For example:
In my C program in a point I say:
if (a==1) {system ("/home/alex/scripts/prog/macchanger2.sh"); system("/home/alex/Qt/hak/hak);}
Well, the problem is that the macchanger2.sh is something like this:
echo "Type your new mac address:"
echo
macchanger -m yy:yy:yy:yy:yy:yy wlan0

How can I tell the script to let the user type his preferable mac address and put it where yy:yy:yy:yy:yy:yy is?
I hope I were understandable enough....If not, plz let me know....

---

### Post by Odd-rationale on 2010-02-04
See if these links helps:

[http://linuxcommand.org/wss0110.php](http://linuxcommand.org/wss0110.php)

[http://www.linuxconfig.org/Bash_scripting_Tutorial#6-reading-user-input](http://www.linuxconfig.org/Bash_scripting_Tutorial#6-reading-user-input)

---

### Post by ibuclaw on 2010-02-04
Why are you doing system calls in C?

You might as well just write it in a scripting language, it's much more flexible to let you do what you want too.

Regards
Iain

---

### Post by hakermania on 2010-02-04
> **Odd-rationale said:**
> See if these links helps:

[http://linuxcommand.org/wss0110.php](http://linuxcommand.org/wss0110.php)

[http://www.linuxconfig.org/Bash_scripting_Tutorial#6-reading-user-input](http://www.linuxconfig.org/Bash_scripting_Tutorial#6-reading-user-input)

extremely helpful!!!
So, "read" is like "scanf"
Ouao!
Excellence!!!
 I am thrilled with my 1st steps in programming...!Ubuntu formus rock!:popcorn:

---

### Post by Odd-rationale on 2010-02-04
No problem.

If that answers your question, consider marking this thread as solved.

---

### Post by hakermania on 2010-02-04
Thanks to you my program is now complete! It is a prog that uses macchanger and aircrack-ng and have the purpose to make your life easier!!! Yours :D
oh, and something else, how do I mark the thread as solved?

link to file:
h t t p:// rapidshare . com/files/345976934/hak.tar

---

### Post by Odd-rationale on 2010-02-04
> **hakermania said:**
> 
oh, and something else, how do I mark the thread as solved?


At the top of the thread, click on Thread Tools --> Mark as Solved.

---

