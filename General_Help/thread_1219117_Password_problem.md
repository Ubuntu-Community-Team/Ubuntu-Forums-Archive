---
title: "Password problem"
date: 2009-07-21
forum: General Help
---

### Post by dlw on 2009-07-21
Just installed 9.04 remix on AA1 this am.
Enter password during install no problems reported.
Now the password does not work.
I am sure I'm using the right password.
The caps lock was not on.

How do I solve this short of reinstalling?

dlw

---

### Post by philcamlin on 2009-07-21
ahah jeres what you do 

1. Turn off your computer.
2. Tap it 3 times
3. Say your favorite magic word.
---- If that doesn't fix your problem, do the steps below...  #-o 
4. Turn your computer on.
5. Press ESC at the grub prompt.
6. Press e for edit.
7. Highlight the line that begins kernel ........., press e
8. Go to the very end of the line, add rw init=/bin/bash
9. press enter, then press b to boot your system.
10. Your system will boot up to a passwordless root shell.
CAUTION: This is a FULL ROOT SHELL! You can damage your system if not careful!
11. Type in passwd <username>. Set your password.
12. Type in reboot.
NOTE: steps 1-3 may help at this point.
:popcorn:

---

### Post by dlw on 2009-07-21
Well, after several attempts at steps 1,2 and 3 I gave up and continued.
All goes well untill step 11.
I type in 'passwd ' then 'username'; press enter.
at 'Enter new password' I type in the first letter of the new password and it skips to 'Retype new password.
The same happens at 'Retype new password'.
Then, I can not enter anything at the # prompt.
I have to switch off the computer to start over.

Any ideas?

dlw

---

### Post by michy99 on 2009-07-21
I hope this doesn't sound completely stupid, but you are typing your username and not the word 'username', right?

---

### Post by dlw on 2009-07-21
Yes, I am.
However, the one letter password works.

dlw

---

### Post by danp85 on 2009-07-21
I'm having the same problem. I installed ubuntu on a new computer a few weeks ago, but didn't get around to using it until today - and during that time I forgot the password, and possibly the username too. D'oh! :D
 
When I get the root shell, I type in exactly what you said: passwd <Daniel> and hit enter... and the response I get is bash: syntax error near unexpected token 'newline'
 
What's this mean?
 
(and if in fact I don't have the correct username either, how would I go about fixing that?)

---

### Post by sisco311 on 2009-07-21
[http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by merlinus on 2009-07-21
Don't put the brackets around Daniel.

```
passwd Daniel
```To find your username

```
ls /home
```

---

### Post by ronao76 on 2009-07-21
I also forgot my password. I turned the computer on. Clicked Esc when it got started. "MBR 2FA:_" comes up. It will not allow me to input 'e' or anything else. 
This is my new 9" mini and I'm already not liking ubuntu.
Please help.

---

### Post by prem1er on 2009-07-21
> **ronao76 said:**
> I also forgot my password. I turned the computer on. Clicked Esc when it got started. "MBR 2FA:_" comes up. It will not allow me to input 'e' or anything else. 
This is my new 9" mini and I'm already not liking ubuntu.

Switch to Windows.

---

### Post by michy99 on 2009-07-21
> **ronao76 said:**
> I also forgot my password. I turned the computer on. Clicked Esc when it got started. "MBR 2FA:_" comes up. It will not allow me to input 'e' or anything else. 
This is my new 9" mini and I'm already not liking ubuntu.
Please help.

The dell mini 9 set up the boot menu with a time out of 0. Really dumb. To get into the boot menu, when you get to the MBR 2FA:_ screen, press Enter and then Esc very fast. You might have to do it a couple of times before you get it.

---

### Post by ronao76 on 2009-07-21
Thank you for your help. However, now I can't find the original post on passwords!
What do I enter now that I have "root@____:~#  ?

---

### Post by merlinus on 2009-07-21
```
passwd username
```

username is your actual name.

---

### Post by ronao76 on 2009-07-21
It says "command not found" when I put in my name

---

### Post by sisco311 on 2009-07-21
> **ronao76 said:**
> It says "command not found" when I put in my name

instead of editing the kernel line in the grub menu just select the *Recovery Mode*. for more info please read the link in my previous post.

---

### Post by ronao76 on 2009-07-22
I could not find your earlier thread.
I there anyone in the DFW metroplex with whom I could meet to fix this problem?

---

### Post by sisco311 on 2009-07-22
> **ronao76 said:**
> I could not find your earlier thread.
I there anyone in the DFW metroplex with whom I could meet to fix this problem?

[http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by sisco311 on 2009-07-22
> **philcamlin said:**
> ahah jeres what you do 

1. Turn off your computer.
2. Tap it 3 times
3. Say your favorite magic word.
---- If that doesn't fix your problem, do the steps below...  #-o 
4. Turn your computer on.
5. Press ESC at the grub prompt.
6. Press e for edit.
7. Highlight the line that begins kernel ........., press e
8. Go to the very end of the line, [COLOR="Red"]remove ro quiet splash[/COLOR] and add rw init=/bin/bash
9. press enter, then press b to boot your system.
10. Your system will boot up to a passwordless root shell.
CAUTION: This is a FULL ROOT SHELL! You can damage your system if not careful!
11. Type in passwd <username>. Set your password.
12. Type in reboot.
NOTE: steps 1-3 may help at this point.
:popcorn:

fixed :)

---

### Post by ronao76 on 2009-07-22
I'm not sure what this 'grub' prompt is. When I press 'esc' after turning the computer on, I get MBR 2FA:  Then it will not allow me to enter 'e' or anything else. 
As you can tell, I am not a computer programer. 
I dislike ubuntu very much.

---

### Post by michy99 on 2009-07-22
Once again, when you are at the MBR 2FA: screen, press Enter and then Esc very fast to get to the Grub menu. Then follow this page:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by ronao76 on 2009-07-23
Thank you. I finally got it.
Now I need to get it back on my home wireless network.

---

