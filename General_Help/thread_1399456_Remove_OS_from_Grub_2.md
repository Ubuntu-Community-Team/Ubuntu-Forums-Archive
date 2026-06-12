---
title: "Remove OS from Grub 2"
date: 2010-02-05
forum: General Help
---

### Post by JetSirus on 2010-02-05
I have Grub 2 and need to remove an OS from the list.  I currently have Ubuntu 8.10 and 9.10 along with WinXP installed.  I want to leave Ubuntu 8.10 installed but remove it from the Grub 2 menu.  How can I do this?

Thanks in advance for any help.

---

### Post by ratcheer on 2010-02-05
Here is an excellent thread on doing things in grub2.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Tim

---

### Post by Leppie on 2010-02-05
on which partition is your hardy install?

---

### Post by JetSirus on 2010-02-05
Thanks for the help there, but that article doesn't say how to omit/exclude an OS from the menu without completely coding the menu from scratch.  Is there a simple non-day long solution for removing a single entry from Grub 2 or will I have to roll back to grub 1?

---

### Post by JetSirus on 2010-02-05
> **Leppie said:**
> on which partition is your hardy install?

/dev/sda3

---

### Post by Leppie on 2010-02-05
> **JetSirus said:**
> Thanks for the help there, but that article doesn't say how to omit/exclude an OS from the menu without completely coding the menu from scratch.  Is there a simple non-day long solution for removing a single entry from Grub 2 or will I have to roll back to grub 1?
you will have to amend a script, but it shouldn't  be too hard ;)

---

### Post by JetSirus on 2010-02-05
> **Leppie said:**
> you will have to amend a script, but it shouldn't  be too hard ;)

LOL.  Grub 2 = Fail.  I understand and appreciate all the hard work the community has done and continues to do on Grub 2, but this simple problem and the horrendous solution just shows that there is still work to be done before it's ready for prime time.

Thanks any way, I believe it will be MUCH simpler to just roll back to an earlier, less obtuse version of Grub.

---

### Post by bcbc on 2010-02-05
You can create a custom menu with only a select number of options (I have two - the lastest linux kernel and windows) in all of 10-15 minutes thanks to meierfra's easy to follow guide. The original menu with all your boot options can be hidden unless you need it. This is probably simpler than reverting to the old grub.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu")

---

### Post by JetSirus on 2010-02-05
> **bcbc said:**
> You can create a custom menu with only a select number of options (I have two - the lastest linux kernel and windows) in all of 10-15 minutes thanks to meierfra's easy to follow guide. The original menu with all your boot options can be hidden unless you need it. This is probably simpler than reverting to the old grub.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu")

Thank you so much, that is a much better solution compared to rollback or scripting.

---

### Post by Leppie on 2010-02-05
> **JetSirus said:**
> Thank you so much, that is a much better solution compared to rollback or scripting.
this actually involves more scripting than modifying the 30_os-prober script, which consists of adding 3 or 4 (if you want to add a comment for the modification) lines ;)

---

### Post by JetSirus on 2010-02-06
> **Leppie said:**
> this actually involves more scripting than modifying the 30_os-prober script, which consists of adding 3 or 4 (if you want to add a comment for the modification) lines ;)

Actually, the other is cut and paste with minor easily understandable changes.  While what you mention is much less friendly on those not in the know.  The 3 lines of code you allude to, yet fail to elaborate on, would have taken me an entire day to get working on my own.  I appreciate your response (honestly), but it's helpfulness is questionable.

---

### Post by Leppie on 2010-02-07
> **JetSirus said:**
> While what you mention is much less friendly on those not in the know.
the code is actually quite simple and rather easy to understand.

> **JetSirus said:**
> The 3 lines of code you allude to, yet fail to elaborate on, would have taken me an entire day to get working on my own.  I appreciate your response (honestly), but it's helpfulness is questionable.
it's attitudes like yours that stop me from providing the solution straight away. if you had done a little research (even going through old posts of mine) you most probably would've found those 3 lines already. it's easy to complain and say that things are so very difficult to do without knowing what is really proposed.
learn to accept proposals without rejecting the idea beforehand.

---

### Post by JetSirus on 2010-02-07
> **Leppie said:**
> the code is actually quite simple and rather easy to understand.


it's attitudes like yours that stop me from providing the solution straight away. if you had done a little research (even going through old posts of mine) you most probably would've found those 3 lines already. it's easy to complain and say that things are so very difficult to do without knowing what is really proposed.
learn to accept proposals without rejecting the idea beforehand.

I apologize if I came off as rude.  That wasn't my intention.  I simply meant that I had looked into the solution you provided (for couple hours) and it was much more difficult for **me** to understand than the other solution.

What I meant about the code you mentioned, was that it would have been much more helpful to me if you had simply pointed me to either a solution or some information on a starting point for me to figure out how to solve it myself.  Basically I meant (and I swear I mean this as helpful criticism) that you hadn't helped me in anyway other than bumping the thread.  You see, I knew I could change that script before I posted this thread.  I may not have communicated that properly and that's my fault.  I appreciate the fact that you took time to reply, but if you enjoy helping people, you should probably do more than say that there is a solution, and that you know how to do it easily.

A good comparison would be me asking how to build a picket fence and you telling me with wood, nails, hammer and saw.  You have communicated nothing to me that is helpful.  With that I know what I need, but not how to accomplish my goal.  Where as if you had said that I should look into a book on woodworking and pointed me to a good one, I would have really had something to work with.

Once again, I apologize for sounding rude, it wasn't my intention.

---

### Post by jon890 on 2010-02-07
OS Ubuntu 9.1
Kernel 2.6.31-19
Any easy way to remove old kernels i.e 2.6.31-17 from grub menu.
go to /boot folder, create directory /old
move all old kernel files from /boot to /boot/old
run sudo update-grub
old kernels are still retained but removed from menu.

---

### Post by Leppie on 2010-02-07
> **JetSirus said:**
> I apologize if I came off as rude.  That wasn't my intention.
don't worry, no offense taken.

> **JetSirus said:**
> I simply meant that I had looked into the solution you provided (for couple hours) and it was much more difficult for **me** to understand than the other solution.
if you haven't been able to find a simple solution to this, it doesn't necessarily mean the simple solution doesn't exist.

> **JetSirus said:**
> What I meant about the code you mentioned, was that it would have been much more helpful to me if you had simply pointed me to either a solution or some information on a starting point for me to figure out how to solve it myself.  Basically I meant (and I swear I mean this as helpful criticism) that you hadn't helped me in anyway other than bumping the thread.
if you hadn't rejected the proposal straight away without telling us that you had already looked into modifying the grub scripts, i probably would've posted the solution in my 2nd post... often finding the solution isn't the real solution, but finding a way to ask the right questions providing the right information.

> **JetSirus said:**
> You see, I knew I could change that script before I posted this thread.  I may not have communicated that properly and that's my fault.  I appreciate the fact that you took time to reply, but if you enjoy helping people, you should probably do more than say that there is a solution, and that you know how to do it easily.
if you had gone through my posts, you would've known that i first want to assure i fully understand what the OP wants as this often is different from what the OP is asking for. as stated before, just asking a question will not guarantee you will get the answer you're looking for.

> **JetSirus said:**
> A good comparison would be me asking how to build a picket fence and you telling me with wood, nails, hammer and saw.  You have communicated nothing to me that is helpful.  With that I know what I need, but not how to accomplish my goal.  Where as if you had said that I should look into a book on woodworking and pointed me to a good one, I would have really had something to work with.
in the same way we can say that you have provided no information at all on what you have done and tried to reach your objective. it's easy saying that people do not want to help you properly and at the same time refusing/omitting to provide information that would help others to help you.

> **JetSirus said:**
> Once again, I apologize for sounding rude, it wasn't my intention.
no offense taken

so if you only want to hide hardy from your grub menu, open your 30_os-prober script with a text editor:
```
gksudo gedit /etc/grub.d/30_os-prober
```
now look for the following section and add the part in red, you can just copy and paste:
```
      for LINUX in ${LINUXPROBED} ; do
        LROOT="`echo ${LINUX} | cut -d ':' -f 1`"
        LBOOT="`echo ${LINUX} | cut -d ':' -f 2`"
        LLABEL="`echo ${LINUX} | cut -d ':' -f 3 | tr '^' ' '`"
        LKERNEL="`echo ${LINUX} | cut -d ':' -f 4`"
        LINITRD="`echo ${LINUX} | cut -d ':' -f 5`"
        LPARAMS="`echo ${LINUX} | cut -d ':' -f 6- | tr '^' ' '`"

        [COLOR=Red]#don't add Hardy to the boot menu
        if [ "${LROOT}" = "/dev/sda3" ]; then
          continue
        fi[/COLOR]
```
save and exit the file, then run update-grub:
```
sudo update-grub
```
and that's it ;)

---

### Post by JetSirus on 2010-02-07
> **Leppie said:**
> don't worry, no offense taken.


if you haven't been able to find a simple solution to this, it doesn't necessarily mean the simple solution doesn't exist.


if you hadn't rejected the proposal straight away without telling us that you had already looked into modifying the grub scripts, i probably would've posted the solution in my 2nd post... often finding the solution isn't the real solution, but finding a way to ask the right questions providing the right information.


if you had gone through my posts, you would've known that i first want to assure i fully understand what the OP wants as this often is different from what the OP is asking for. as stated before, just asking a question will not guarantee you will get the answer you're looking for.


in the same way we can say that you have provided no information at all on what you have done and tried to reach your objective. it's easy saying that people do not want to help you properly and at the same time refusing/omitting to provide information that would help others to help you.


no offense taken

so if you only want to hide hardy from your grub menu, open your 30_os-prober script with a text editor:
```
gksudo gedit /etc/grub.d/30_os-prober
```
now look for the following section and add the part in red, you can just copy and paste:
```
      for LINUX in ${LINUXPROBED} ; do
        LROOT="`echo ${LINUX} | cut -d ':' -f 1`"
        LBOOT="`echo ${LINUX} | cut -d ':' -f 2`"
        LLABEL="`echo ${LINUX} | cut -d ':' -f 3 | tr '^' ' '`"
        LKERNEL="`echo ${LINUX} | cut -d ':' -f 4`"
        LINITRD="`echo ${LINUX} | cut -d ':' -f 5`"
        LPARAMS="`echo ${LINUX} | cut -d ':' -f 6- | tr '^' ' '`"

        [COLOR=Red]#don't add Hardy to the boot menu
        if [ "${LROOT}" = "/dev/sda3" ]; then
          continue
        fi[/COLOR]
```
save and exit the file, then run update-grub:
```
sudo update-grub
```
and that's it ;)

And thank you!  Now that the communication issues were cleared up we (actually you) found a solution to the issue.    :D

---

### Post by Leppie on 2010-02-07
> **JetSirus said:**
> And thank you!  Now that the communication issues were cleared up we (actually you) found a solution to the issue.    :D
i found this solution a while ago, it's simple and effective.
other menu tweaks can be obtained in a fairly easy way as well. anyways, try my suggestion and see if you like it. you can always revert to the other guides you found ;)

---

