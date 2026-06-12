---
title: "Synaptic without password prompt"
date: 2010-05-13
forum: General Help
---

### Post by satish_j on 2010-05-13
Is there any way to open synaptic package manager(or for that matter,any other GUI application)without pwd prompt.???

---

### Post by Ampi on 2010-05-13
I don think so. But I think that if you loging once and close it, the next time it is logged in!

---

### Post by wojox on 2010-05-13
The answer lies in here: [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by satish_j on 2010-05-13
> **wojox said:**
> The answer lies in here: [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

Thanks for the link...some queries on same now...the link says the basic syntax for user specification is:
```

<user list> <host list> = <operator list> <tag list> <command list>

```
Can i omit <operator list> from above??
Also,what is the command running in background when we start synaptic??

---

### Post by wojox on 2010-05-13
I was thinking more along this line 

Use 'ALL=(ALL) NOPASSWD:ALL' if you don't want to be prompted a password.

---

### Post by ryan858 on 2010-05-13
There should be a line in sudoers saying "**%admin ALL=(All) ALL**" (I think). Change it to this:

**%admin  ALL=NOPASSWD: /usr/sbin/synaptic**

That should work. If it doesn't then try the same with the line "<yourname> ALL=(ALL) ALL" and then try with the %sudo line...

Also, I don't know if you should *change* the lines or just *copy* them and *then* change them... Can someone verify please?

---

### Post by satish_j on 2010-05-13
> **ryan858 said:**
> Change it to this:

**%admin  ALL=NOPASSWD: /usr/sbin/synaptic**



I dint think so..That will only allow synaptic command to be run without password and too,the only command for admin group??

---

### Post by satish_j on 2010-05-13
Can i use foll:
```

User_Alias PowerUsers = satish

```
and then,
```

PowerUsers All=(All)NOPASSWD: /usr/sbin/synaptic

```
Is there a space between ')' and NOPASSWD???Also,colon ':' is really required??

---

### Post by Rubi1200 on 2010-05-13
If you don't mind me asking, why would you want to try and circumvent the built-in security layers that help make Ubuntu (and Linux) safer than other OS's?

If it is a matter of convenience, then I think you are asking for trouble.

Read this please before doing anything drastic:

[http://www.psychocats.net/ubuntu/security#sudomakessense](http://www.psychocats.net/ubuntu/security#sudomakessense)

---

### Post by Soul-Sing on 2010-05-13
> **rubi1200 said:**
> if you don't mind me asking, why would you want to try and circumvent the built-in security layers that help make ubuntu (and linux) safer than other os's?

If it is a matter of convenience, then i think you are asking for trouble.

Read this please before doing anything drastic:

[http://www.psychocats.net/ubuntu/security#sudomakessense](http://www.psychocats.net/ubuntu/security#sudomakessense)

+1

---

### Post by satish_j on 2010-05-13
> **Rubi1200 said:**
> If you don't mind me asking, why would you want to try and circumvent the built-in security layers that help make Ubuntu (and Linux) safer than other OS's?

To be very frank,i do not like certain features of Ubuntu..
What is the point in asking password to a user created at time of installation(i.e an admin user)..
The term 'admin' does not fit correctly in certain scenario..
Password prompts at each and every basic level causes frustation sometimes...
So,i need to disable these password-prompts at certain levels where i seem security is not that crucial.
I mean there is no harm in disabling the prompt at synaptic level..user can only install/remove the packages...
also,this ensures synaptic runs w/o pwd ONLY FROM MY ID...other users will get the prompt as usual...

---

### Post by wojox on 2010-05-13
Here's one more link for you [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

We are really not suppose to discuss enabling or disabling root on the forums.

---

### Post by Rubi1200 on 2010-05-13
The forum policy on root/sudo is outlined here:

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

I was not, in any form or manner, attempting to instruct the OP regarding root/sudo usage, merely to point out that bypassing sudo for the sake of convenience is potentially extremely dangerous.

> To be very frank,i do not like certain features of Ubuntu..
What is the point in asking password to a user created at time of installation(i.e an admin user)..
The term 'admin' does not fit correctly in certain scenario..
Password prompts at each and every basic level causes frustation sometimes...
So,i need to disable these password-prompts at certain levels where i seem security is not that crucial.
I mean there is no harm in disabling the prompt at synaptic level..user can only install/remove the packages...
also,this ensures synaptic runs w/o pwd ONLY FROM MY ID...other users will get the prompt as usual...

Once you start by disabling password authentication for Synaptic, where does it end...?

Again, I implore that you read the links posted by myself and wojox and that you think long and hard BEFORE taking action that could potentially cause serious harm to your system.

From the same thread as I linked to (written by bodhi.zazen, one of the security gurus here):

> Sudo offers a finer grain of control over root access and offers options such as insults and lectures. Insults, at the name implies, will insult users who fail to enter the proper password.

Care must be taken when configuring sudo and IMO, as it affects security, is one of the exceptions to my "RTFM" position. I strongly advise you read and understand the features and options of sudo before you alter it's default configuration.



General tips : 
It should go without saying, you configure sudo at your own risk. Always confirm the advice you receive.

I STRONGLY advise against weakening your overall security. Keep in mind, if you are connected to the internet you are not the only potential user (as any network monitoring application will show in short order).

Back up your /etc/sudoers before you edit the file.

---

### Post by satish_j on 2010-05-13
> **wojox said:**
> 
We are really not suppose to discuss enabling or disabling root on the forums.

Well,iam not aware of this...But,i do not see any logic behind this as we are not discussing any hacking or illegal stuff:confused:
BTW,can you pls comment on the user_alias and user specification i mentioned in pt 8??

---

### Post by Rubi1200 on 2010-05-13
Just in case our paths crossed when posting, I urge you read what I wrote just before you posted.
Thanks.

---

### Post by satish_j on 2010-05-13
> **Rubi1200 said:**
> Just in case our paths crossed when posting, I urge you read what I wrote just before you posted.
Thanks.

I dont understand why some users are so afraid of using root account??
Iam not doing any extremely dangerous activity like removing the prompt from editing system files in /etc/bin directories,etc...
Iam well aware of the risks involved and i intend to continue the same for certain commands.
Now,if you can help me out with command syntax to be entered in sudoers file,it will be very helpful..

---

### Post by satish_j on 2010-05-14
requesting help from experts on this...i do not want to continue with the command unless given positive signal by some of you seniors...
Also,i tried yesterday visudo..it is very confusing for newbies..can anyone guide to an good tutorial on same???

---

### Post by Firbewn9 on 2011-01-23
* sudo visudo, add at the end 

```
username      ALL=(ALL) NOPASSWD: ALL
```

*in terminal 

```
alacarte
```Now pick up a program. For egzample synaptic and open "properities". Change from

```
gksu --description /usr/share/applications/synaptic.desktop /usr/sbin/synaptic


```to 

```
gksudo --description /usr/share/applications/synaptic.desktop /usr/sbin/synaptic
```I don't have time to look for "software-center" now in alacarte.
If it would be problematic, you can always add it yourself. Make new position and put 

```
gksudo software-center
```in command field.

Restart X (log out, log in) for changes to take effect.

If you will come across the 'original' software-center let me know.

Have fun.

---

### Post by mastablasta on 2011-01-23
> **satish_j said:**
> I dont understand why some users are so afraid of using root account??
Iam not doing any extremely dangerous activity like removing the prompt from editing system files in /etc/bin directories,etc...
Iam well aware of the risks involved and i intend to continue the same for certain commands.


well the problem is that viruses or malware could run itself under root as the malicious programme doesn't need any command form the user to be run.

basically if you get some malicious programme (for example someone send it to you on purpose etc.) it can execue itself automaticly and you probably won't even know it it running. while if you use sudo the programme will have to ask your permission which is verified by your user password.

but obviously you already know about this security this risk.

not to mention sudo is active for a wghile and is used only when doing changes to system files. as a result i haven't used it or needed in a while.

---

### Post by phocks on 2011-07-28
Here's my solution anyway. Just being helpful instead of jerking everyone around like everyone else on the internet when I tried to look up how to do this:

1. Log in
2. Open Terminal and type sudo passwd root
3. Type a root password, and confirm it
4. Log out
5. Log in as root using the password
6. Edit /etc/passwd (nano, or vi in a terminal)
7. Find your username and make the two numbers 0:0
8. Log out of root
9. Log back in to your account
10. No more annoying popup password authentication prompts
11. Reverse it once you've stopped playing around with the system

Be careful kids ;)

---

