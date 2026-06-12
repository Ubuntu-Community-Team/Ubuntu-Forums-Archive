---
title: "Checking suspicious files."
date: 2011-10-10
forum: General Help
---

### Post by DeathByLinux on 2011-10-10
Hello,
       I am downloading a file that seems to good to be true. I want to run it, but I am thinking that it might be a virus and if I run it using WINE I will get virused. 
I think there was a program for Linux that allowed you to check individual files for viruses, but I don't remember its name. Can anyone suggest a program or give me any advice? Thanks!
-DeathbyLinux

---

### Post by jazzon on 2011-10-10
lol...virus fears
clam, AV suite for linux

---

### Post by DeathByLinux on 2011-10-10
Yeah, I am a noob. :( 
From my understanding if I execute a program, using my root access, I will get virused, will I not? 
The program that I am downloading is a windows .exe file and I will need to use WINE to use it. If it is virused, will it affect Linux or what?
-DeathbyLinux

---

### Post by jazzon on 2011-10-10
nah, could (maybe) effect wine but unless your in a wubi environment (which I am totally unfamiliar with so i can't help you if you are) then a virii couldn't hurt your linux install UNLESS it was written for linux.  And since you don't need to be root to use wine (it will even complain if you do run it as root) then don't be root.  Just execute it as a normal user.

Virii have to be written to attack certain code bases.  Since most of the world runs windows, it follows that most virii are written for windows.  Also the file your after is a windows exe, so it follows that any virus in it is made for windows .

Since windows and linux use two totally different code bases/file structures a virus written for one would likely be harmless on the other.

If your wine actually points to a wrkin install of windows however, that could change all the rules....

The virus might be able to infect your windows OS, but it could only be active when wine was running, or you actually booted to windows.  Like i said origianally, clam.  Its a made for windows virus scanner.  You can find it as clamav in the package manager of your choice, or ```
sudo apt-get install clamav
```
Best of luck.

---

### Post by Dangertux on 2011-10-10
I would not recommend ClamAV it is essentially useless. It's detection rate on common threats is less than 70%

That being said -- running your application under Wine with root privileges is a very bad idea. Although , you would be surprised how much Wine Server actually has access to, it is actually possible to escalate via a Windows based shell under Wine. The reason this is possible is because Wine is not an emulator, it is an interpreter. It attempts to translate what your Windows application is saying into Linux system calls, it actually does a pretty good job at it.

If the application seems too good to be true it probably is. Use common sense ultimately. If you would like more information on how Windows based malware can access your Linux system if executed you may read[ this article ]("http://dangertux.wordpress.com/2011/09/17/the-truth-about-windows-malware-wine-and-ubuntu/")that I wrote illustrating how it can happen. 

This is a rare situation, and is not likely to occur, however it is wise to educate yourself on the possibilities. You could always consider running the file through something like [http://www.virustotal.com](http://www.virustotal.com) to get a more complete picture. Since the Linux based Anti-Malware solutions are pretty much garbage.

Hope that helps.

---

### Post by scorp123 on 2011-10-10
> **DeathByLinux said:**
> I am downloading a file that seems to good to be true.  Then it probably is. So ... **don't run it!** Use common sense!

---

### Post by jazzon on 2011-10-10
@danger
Didn't realize clam av had such a low detection rate.  Could you by chance recommend a better one (linux variety) I am looking into setting up a mailserver (to learn how) and want to have it do auto checking, so I might as well learn a good one..

Also excellent point about Interpretor and not an emulator.  That thought never occurred to me.

Excellent advice to OP, unlike mine..... <cry>

---

### Post by oldos2er on 2011-10-10
One wonders what this mysterious Windows file is named, and what site it came from.

---

### Post by Dangertux on 2011-10-10
> **jazzon said:**
> @danger
Didn't realize clam av had such a low detection rate.  Could you by chance recommend a better one (linux variety) I am looking into setting up a mailserver (to learn how) and want to have it do auto checking, so I might as well learn a good one..

Also excellent point about Interpretor and not an emulator.  That thought never occurred to me.

Excellent advice to OP, unlike mine..... <cry>

Honestly, in terms of Free as in beer there really isn't a whole lot in terms of comparable Anti-malware available for Linux. There are some here that swear by ClamAV and say it provides good results in terms of email scanning. I can't say my experiences have been the same. Note the testing I've done with it though was intentionally trying to bypass it. So I don't know your mileage may vary.

In terms of the most secure solution I would recommend a proprietary hardware anti-malware solution, unfortunately that is outside the grasp of those making less than high 6 figures :-/

From what I've seen of the "Free" solutions avg has the best detection rate but it is still abysmally low compared to it's Windows counterpart. Avast is supposedly good, however updating Avast's definitions in Ubuntu is iffy as it segfaults often. So it's not the most stable solution.

I think anti-malware solutions on Linux and Ubuntu in particular have a long way to go.

Hope that helps.

> **oldos2er said:**
> One wonders what this mysterious Windows file is named, and what site it came from.

As do I

---

### Post by DeathByLinux on 2011-10-10
Okay, so this is what I did:
I used clam before I read Danger's response against it, and it tested negative for virus. I then tried to use WINE to run it and it kept crashing because it said the following: (See attachment)

Anyway, so I thought that this was due to the fact that I had WINE set on Windows 95, which I changed to XP, but it was not. The program crashed in installation no matter what I did. 
So, I took a dive in the deep-end and just took the file and put it on my windows computer and it worked fine on there, without any viruses. 
I guess the main purpose of this thread is served: the file was not virused. I have to figure out why WINE is so finicky, but that is another thread for another time. 
I will leave this thread open for any last closing remarks and then save it as "Solved."
Thanks for all your input, guys. 
-DeathbyLinux

---

### Post by haqking on 2011-10-10
> **DeathByLinux said:**
> Okay, so this is what I did:
I used clam before I read Danger's response against it, and it tested negative for virus. I then tried to use WINE to run it and it kept crashing because it said the following: (See attachment)

Anyway, so I thought that this was due to the fact that I had WINE set on Windows 95, which I changed to XP, but it was not. The program crashed in installation no matter what I did. 
So, I took a dive in the deep-end and just took the file and put it on my windows computer and it worked fine on there, without any viruses. 
I guess the main purpose of this thread is served: the file was not virused. I have to figure out why WINE is so finicky, but that is another thread for another time. 
I will leave this thread open for any last closing remarks and then save it as "Solved."
Thanks for all your input, guys. 
-DeathbyLinux

ek is a keylogger and so why are you trying to install it and also keyloggers are often seen as trojans

---

### Post by Dangertux on 2011-10-10
> **haqking said:**
> ek is a keylogger and so why are you trying to install it and also keyloggers are often seen as trojans

Yep it is -- here is some info on it if you'd like : [http://www.symantec.com/security_response/writeup.jsp?docid=2005-071414-1428-99](http://www.symantec.com/security_response/writeup.jsp?docid=2005-071414-1428-99)

Good luck , most current Windows AV should detect and remove it.

---

### Post by DeathByLinux on 2011-10-10
Is Ubuntu susceptible to being keylogged?

---

### Post by Dangertux on 2011-10-10
> **DeathByLinux said:**
> Is Ubuntu susceptible to being keylogged?

Of course it is, but you would need a linux keylogger. Why are you trying to key log? This may or may not be something we can support here?

---

### Post by haqking on 2011-10-10
> **DeathByLinux said:**
> Is Ubuntu susceptible to being keylogged?

as stated above yes of course but not with a windows keylogger.

however in this instance as you are knowingly downloading potential malware i would be inclined to refer you to your own signature and take heed ;-)

peace

---

### Post by oldos2er on 2011-10-10
[S]Closed for review.[/S]

Closed permanently. We can not condone potentially illegal activity e.g. the use of keyloggers here.

---

