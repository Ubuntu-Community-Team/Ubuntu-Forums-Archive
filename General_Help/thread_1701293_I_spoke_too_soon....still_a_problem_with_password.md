---
title: "I spoke too soon....still a problem with password"
date: 2011-03-06
forum: General Help
---

### Post by Amber2011 on 2011-03-06
:confused::confused:Hi I am back I thought I had this resolved, but not quite. I disabled my sign in screen, then all af a sudden it popped back, only it will not accept my password. I did not forget what it is, it just will not work. I use the following procedure to get on line.

Black boot in page
2nd option:Ubuntu with Linux 2.6.35-27 generic recovery mode
Recovery menu>last option>netroot drop to root shell prompt with networking
ls /home
startx>then I get on-line

If I type my password in any form it says it does not exist or command not found.
Anyway I have to do this every-time to get on-line. Then at the button of screen where my ID should be, it says "root" instead. How can I fix it? It is driving me nuts now but I think It is almost there. Thanks in advance. I will show a pic of the root thing, after I get rid of that I should be good to go. Also in this mode it will not save anything like mail accounts and settings so I can't use it this way.

---

### Post by nothingspecial on 2011-03-06
Go back to the root shell and type

```
passwd amber
```

and reset your password

change amber for  your actual username

---

### Post by mcduck on 2011-03-06
Booting into recovery mode signs you in as root, not as your own user. You shouldn't be starting the desktop from there at all.

Have you tried changing your user's password from the recovery mode, and then signing in from the normal boot?

To change your password, boot into recovery mode, select the root shell option, and then run "passwd *username*" (using your normal account's username, of course) and set yourself a new password. Then run "reboot" and this time just let the system boot into normal mode and try to log in.

---

### Post by Amber2011 on 2011-03-06
mcduck, 

That seemed like it was going to work, it said password accepted and all that. But the black screen would not go away, I kept getting nonsense. I could not get out of it, after a while I think I typed exit then that blank black screen came up with the white blinking curer and asked me for the same junk and took me nowhere.

I am new to this maybe I missed a step. But it said password accepted.

---

### Post by mcduck on 2011-03-06
I can't really help unless you are a bit more specific...

What "black screen"? What "nonsense"? And what "same junk"?

If by black screen you mean the shell itself, that's not supposed to go away when you change the password. Instead you should run the "reboot"-command I suggested, which will restart the computer. And then just select the normal Ubuntu boot from the Grub menu instead of recovery mode and you should be fine.

(Running "exit" will not get you out of recovery mode. Only restarting the computer does that)

---

### Post by Amber2011 on 2011-03-06
I am sorry for the confusing words but that is how I feel. I don't know how to explain it, But I guess just the shell page wanted the right command. Just to be clear when you say Boot do you mean type in boot or find and select boot. Cause I did not see that. Sorry for my ignorance but I have not even learned how to walk here. I appreciate you help.

---

### Post by mcduck on 2011-03-06
> **Amber2011 said:**
> I am sorry for the confusing words but that is how I feel. I don't know how to explain it, But I guess just the shell page wanted the right command. Just to be clear when you say Boot do you mean type in boot or find and select boot. Cause I did not see that. Sorry for my ignorance but I have not even learned how to walk here. I appreciate you help.

Boot as in "restart". After changing the password with the "passwd" command run the "reboot" command and your computer will restart. Then select the normal Ubuntu option instead of the recovery mode.

---

### Post by vivek.pandey on 2011-03-06
> **mcduck said:**
> Booting into recovery mode signs you in as root, not as your own user. You shouldn't be starting the desktop from there at all.

Have you tried changing your user's password from the recovery mode, and then signing in from the normal boot?

To change your password, boot into recovery mode, select the root shell option, and then run "passwd *username*" (using your normal account's username, of course) and set yourself a new password. Then run "reboot" and this time just let the system boot into normal mode and try to log in.

i may not be correct but we can login as our non root user in recovery mode.. when you enter recovery mode after some lines of text you get a menu, if you choose resume
you are asked to login just enter your non root user and the password..
this is possible in my ubuntu 10.10 so i guess it should work with others too

---

### Post by Amber2011 on 2011-03-06
I don't know something is wrong. I am guessing me. Here is the what is going on. after the root screen comes up nothing will happen unless I type in ls /home. It will not accept anything else at this point.
After that my user name comes up in highlighted letters. That is a good thing!
Then the next command line is waiting for me to do something.
It looks like this(my actual user name is here ):~$
Sometimes it looks like this (my actual user name is here):~#
I tried typing in a hundred different things. My password, I tried to create a new password  and all It says is "not found" I tried it over and over. I am ready just to go back to windows, and I really do not want to do that. At least with xp I know how to work on things, I feel like an idiot here. I had to connect on here as the root over and over and I know I am not suppose to.

---

### Post by vivek.pandey on 2011-03-06
> **Amber2011 said:**
> I don't know something is wrong. I am guessing me. Here is the what is going on. after the root screen comes up nothing will happen unless I type in ls /home. It will not accept anything else at this point.
After that my user name comes up in highlighted letters. That is a good thing!
Then the next command line is waiting for me to do something.
It looks like this(my actual user name is here ):~$
Sometimes it looks like this (my actual user name is here):~#
I tried typing in a hundred different things. My password, I tried to create a new password  and all It says is "not found" I tried it over and over. I am ready just to go back to windows, and I really do not want to do that. At least with xp I know how to work on things, I feel like an idiot here. I had to connect on here as the root over and over and I know I am not suppose to.

i guess you should give a try to the recovery mode thing which i told one post above your las post

---

### Post by Amber2011 on 2011-03-06
Yea I will see how that works out for me. Thank you.

---

### Post by Amber2011 on 2011-03-06
neo_aryan,

OK when I try that it says welcome to Ubuntu but then that stupid (my user name):~$ comes back. What should I type it here?

After it said welcome I thought it was fine but the screen just sits there waiting for something.

---

### Post by mcduck on 2011-03-06
> **neo_aryan said:**
> i may not be correct but we can login as our non root user in recovery mode.. when you enter recovery mode after some lines of text you get a menu, if you choose resume
you are asked to login just enter your non root user and the password..
this is possible in my ubuntu 10.10 so i guess it should work with others too

That option simply takes you out of the recovery mode and boots normally instead. (like it even says on the menu, "resume - Resume normal boot")

---

### Post by vivek.pandey on 2011-03-06
i assume you entered the recovery mood selected resume normal boot...then some lines appeared and went and then did you get login prompt? (computer name): something of this sort?

if you are here (username):~$ 
just enter startx you should get a gui

---

### Post by vivek.pandey on 2011-03-06
> **mcduck said:**
> That option simply takes you out of the recovery mode and boots normally instead. (like it even says on the menu, "resume - Resume normal boot")

thanx for this info.. thats why i said i may not be correct . i always thought its a part of recovery only..
thanx for the info
but anyways it works

---

### Post by mcduck on 2011-03-06
> **neo_aryan said:**
> i assume you entered the recovery mood selected resume normal boot...then some lines appeared and went and then did you get login prompt? (computer name): something of this sort?

if you are here (username):~$ 
just enter startx you should get a gui

It makes no sense to do it that way. To get a normal boot just boot normally from the Grub menu, there's no point in selecting the recovery option if you are just going to boot normally anyway, that just adds a pointless extra step and a bunch of fast scrolling text... :)

---

### Post by mcduck on 2011-03-06
> **Amber2011 said:**
> neo_aryan,

OK when I try that it says welcome to Ubuntu but then that stupid (my user name):~$ comes back. What should I type it here?

After it said welcome I thought it was fine but the screen just sits there waiting for something.

You already said that you succesfully ran the "passwd" command in the recovery mode. You have no reason to boot into recovery mode any more. What happens if you use the normal Ubuntu option from the Grub menu (the one with black background and different kernel versions listed)?

Could you please try that and tell what happens?

---

### Post by Amber2011 on 2011-03-06
Yes I have tried many times. After I select Ubuntu from the Grub menu it takes me to the normal desktop page. That is the problem cause  when it does that, I get that sign in screen that will not accept my  password.

And yes if I type in startx from the root that will put me on-line however in the root mode. All was well, till all of a sudden one day I logged on and the dreadful password page showed up. Again I appreciate all this help but Ubuntu is just taking me on a merry-go-round. I think maybe my Ubuntu is broken.

---

### Post by Amber2011 on 2011-03-06
> **mcduck said:**
> You already said that you succesfully ran the "passwd" command in the recovery mode. You have no reason to boot into recovery mode any more. What happens if you use the normal Ubuntu option from the Grub menu (the one with black background and different kernel versions listed)?

Could you please try that and tell what happens?

Yes it appeared that I ran the password correctly, but it was waiting for a command. (my actual user name):~$ I can't get away from that screen.

---

### Post by mcduck on 2011-03-06
> **Amber2011 said:**
> Yes it appeared that I ran the password correctly, but it was waiting for a command. (my actual user name):~$ I can't get away from that screen.

That's where I told you to type "reboot" to get out of the recovery mode and start Ubuntu in normal way.

---

### Post by runeh76 on 2011-03-06
> **Amber2011 said:**
> :confused::confused:Hi I am back I thought I had this resolved, but not quite. I disabled my sign in screen, then all af a sudden it popped back, only it will not accept my password. I did not forget what it is, it just will not work. I use the following procedure to get on line.

Black boot in page
2nd option:Ubuntu with Linux 2.6.35-27 generic recovery mode
Recovery menu>last option>netroot drop to root shell prompt with networking
ls /home
startx>then I get on-line

If I type my password in any form it says it does not exist or command not found.
Anyway I have to do this every-time to get on-line. Then at the button of screen where my ID should be, it says "root" instead. How can I fix it? It is driving me nuts now but I think It is almost there. Thanks in advance. I will show a pic of the root thing, after I get rid of that I should be good to go. Also in this mode it will not save anything like mail accounts and settings so I can't use it this way.


Hi u can log in without password! Check next:
[http://helpdeskgeek.com/linux-tips/automatically-log-into-ubuntu-without-a-password-or-the-login-screen/]("http://helpdeskgeek.com/linux-tips/automatically-log-into-ubuntu-without-a-password-or-the-login-screen/")

Use ur method to change that:
"Black boot in page
2nd option:Ubuntu with Linux 2.6.35-27 generic recovery mode
Recovery menu>last option>netroot drop to root shell prompt with networking
ls /home
startx>then I get on-line"

---

### Post by Amber2011 on 2011-03-06
> **runeh76 said:**
> Hi u can log in without password! Check next:
[http://helpdeskgeek.com/linux-tips/automatically-log-into-ubuntu-without-a-password-or-the-login-screen/](http://helpdeskgeek.com/linux-tips/automatically-log-into-ubuntu-without-a-password-or-the-login-screen/)

Use ur method to change that:
"Black boot in page
2nd option:Ubuntu with Linux 2.6.35-27 generic recovery mode
Recovery menu>last option>netroot drop to root shell prompt with networking
ls /home
startx>then I get on-line"

Yes that is how I have been getting on line, but that puts me in the root mode and not the user mode. I will check out that website, thank you. I will be back later I just got company.

---

### Post by Amber2011 on 2011-03-06
> **runeh76 said:**
> Hi u can log in without password! Check next:
[http://helpdeskgeek.com/linux-tips/automatically-log-into-ubuntu-without-a-password-or-the-login-screen/](http://helpdeskgeek.com/linux-tips/automatically-log-into-ubuntu-without-a-password-or-the-login-screen/)

Use ur method to change that:
"Black boot in page
2nd option:Ubuntu with Linux 2.6.35-27 generic recovery mode
Recovery menu>last option>netroot drop to root shell prompt with networking
ls /home
startx>then I get on-line"

runeh76, I went to that change password page but it opens as a blank page I am unable to select any options cause I can only log in as the root not the user. This whole this is ridiculous, I have been at this 2 days now.

---

### Post by nothingspecial on 2011-03-06
Just do what I said, back on page one. When you have typed your new password twice, just enter through all the room number rubbish. When you get to the end, type ```
restart
``` and away you go. :P

---

### Post by Amber2011 on 2011-03-06
I tried that early on, this is just not worth it. It does however accept my password in safe mode. I just came across that. But if this safe mode is like xp safe mode, it is not where you want to be all the time. Or is ok with Ubuntu I don't expect you guys to spend all this time here on this subject. At least I am here now under my name, just in safe mode, that is all. Thank you all for you help

---

### Post by mcduck on 2011-03-07
> **Amber2011 said:**
> I tried that early on, this is just not worth it. It does however accept my password in safe mode. I just came across that. But if this safe mode is like xp safe mode, it is not where you want to be all the time. Or is ok with Ubuntu I don't expect you guys to spend all this time here on this subject. At least I am here now under my name, just in safe mode, that is all. Thank you all for you help

Have you tried it now, *after* you have successfully changed your password?

(And since you have already changed the password, you don't of course need to do it again. You just had to do the recovery mode+passwd-command -thing *once* to get a working password for your user account. It should work just fine in the normal mode now.)

---

### Post by Amber2011 on 2011-03-07
No, it is still not working. Thanks for asking though. I still can only get on here in safe mode or root I read on another thread of other people having this problem. Some have not been able to log on for weeks. A bug or something. I guess I will find out how to uninstall and try it again in a month or so. Thanks again I appreciate you and everybody else taking time out and helping me.

---

