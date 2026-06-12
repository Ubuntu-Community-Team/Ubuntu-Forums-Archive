---
title: "putty and vista - connection refused"
date: 2009-11-27
forum: General Help
---

### Post by odansky on 2009-11-27
hi everyone,
first time with linux. i'm trying to connect to my ubunto box from my vista box.
 
i tried following this link:
[http://ericleite.com/2009/02/27/how-to-vnc-from-vista-to-ubuntu-local-network/](http://ericleite.com/2009/02/27/how-to-vnc-from-vista-to-ubuntu-local-network/)
 
when i try to run putty - i get connection refused :(
 
i tried telnet to my ubunto box and i seems to be ok.
 
what should i try next?
 
Thanks, Omer

---

### Post by teward on 2009-11-27
***EDIT: Removed because I'm an idiot and didn't read the link.  Forget I posted.***

---

### Post by odansky on 2009-11-27
thanks for your reply.
if by installing ssh-clinet you mean:
"Install SSH **[COLOR=#e4d3a6]- [/COLOR]**Run this command in console: *sudo apt-get install openssh-server*
**[COLOR=#e4d3a6]>[/COLOR]** Activate Remote Desktop **[COLOR=#e4d3a6]- [/COLOR]**Navigate to System -> Preferences -> Remote Desktop.
Turn on three settings: *Allow others users to view your desktop*,* Allow other users to control your desktop*,and *Require the user to enter this password.*(remember this password for later)  "
 
Then i have done this.
 
i am a complete novice when it comes to linux.

---

### Post by Dinodoc on 2009-11-28
Sounds like your ssh server might not be running.

Try: ps -ef | grep sshd 

If it doesn't come up with one running then maybe you just need to start it.  

sudo /usr/sbin/sshd

Then enter your password when it asks you too.

---

### Post by odansky on 2009-11-28
Thanks for you help. i managed to connect to the linux box just by using the VNC viewer only - without trying putty.
and i connect to the box via the local ip and not external ip.
 
 
Now i have another problem - i cannot copy files from one box to another. is there anything i should enable?
 
Thanks, Omer

---

### Post by Dinodoc on 2009-11-28
Unless you set up shares between the 2 computers or install maybe an ftp server on the linux box I am not sure.

VNC is simply a way to show your desktop to other computers, it doesn't allow for copying files from said computer.

You could set a directory on your Vista computer as a shared directory and mount it on the ubuntu computer, then just copy stuff back and forth using that directory, or if you can get ssh working you could use sftp to copy files over using something like filezilla.

Did you try to see if ssh was running on your ubuntu computer?

---

### Post by odansky on 2009-11-28
i ran this: ps -ef | grep sshd 
and it gave me back:
root      7745     1  0 01:33 ?        00:00:00 /usr/sbin/sshd
bla      9000  8961  0 10:44 pts/0    00:00:00 grep --color=auto sshd
 
so i guess its running? or not?

---

### Post by Dinodoc on 2009-11-28
Hmm yeah it appears to be

Only other thing I can think is maybe you have wrong ip for your ubuntu box?  I find it odd the website suggests setting it to the external ip, I usually just ssh to the ip behind my router (from the article ex. 192.168.1.101). (When connecting from one local machine to another)

I think for copying files it might still be easier to set up a share on your Vista box and copy files to it on the ubuntu box.

I haven't used Vista, but I'm hoping it similar to XP, create a folder (say share), then right click on folder and select properties, then go to the Share or Sharing tab. 
Share the folder and create a name and description for it.

In ubuntu, click on Places > Network opens a file browser.
Click on Windows Network follow along til you find your share. Open it and you should be able to copy stuff to it and it will appear in the directory on the windows system.

I have to admit I have never actually done this, but I am hoping this should work for you.

---

### Post by odansky on 2009-11-28
Thanks for all your help!! it was easier than i thought!.
 
As you said what i needed to do was:
 
In ubuntu, click on Places > Network opens a file browser.
Then i found my Vista Comp name. -> Clicked on it.
Enter the username and pwd.
 
Now i am able to copy files with no problems.
 
So simple :)
 
Thank you very much!
 
Omer

---

