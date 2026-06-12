---
title: "Upgrade and login problems"
date: 2010-03-24
forum: General Help
---

### Post by Patrick Lavelle on 2010-03-24
My daughter from New Zealand gave me her Acer Aspire 4315 Laptop/Notebook Linux System in December 2009 so that I could use it in bed on days that I was unable to get out to use my main computer as I am a very ill man. I was able to log into the unit as she just said to me to use her name and password to. I have been able to use the unit on the internet at home and my other daughters home through a home wireless system. I clicked on the Upgrade Icon which it did, I think it went from a 7. something to 8.something All the way through the set up it asked me questions and I just clicked yes thinking that was what I had to do. My problem now is, that when I turn the unit on it asks me for a username and password. I put the details my daughter gave me but it tells me invalid user and password. All I do know is that a friend of my daughter installed the Ubuntu Program onto the Laptop/Notebook. Can anyone tell me how or what I have to do now to be able to use the unit again as I am getting very frustrated with the whole thing. I am not used to using Ubuntu and am totally lost with it as I have always been a Microsoft user.
 
Thanks and any help would be most appreciated.
Patrick Lavelle](*,)

---

### Post by kamaji792 on 2010-03-24
Sorry to hear about your problems.  Not really able to offer much advice but I have a few questions:

[LIST=1]
[*]Was your computer running **ubuntu**?
[*]Can you remember any of the questions it asked you when you thought it was upgrading your laptop?
[/LIST]

You could try this [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

All the best

---

### Post by Patrick Lavelle on 2010-03-24
Thank you for contacting me kamaji792. To your first question, yes my Laptop/Notebook was running Ubuntu. To your second question, I can't remember the questions being asked I just clicked on yes to everything as it was upgrading, sorry I can't tell you anything more than that except that I now have a different screen than I did before I did the upgrade. I thouhgt I was just updating the version that was already on the unit. As for trying to reset the password, well I am unable to do that as I can't get passed the Username and Password login page.
 
Cheers
Patrick Lavelle

---

### Post by kamaji792 on 2010-03-24
Have a look at the link I posted.

The start is as your system is booting press and release the **Esc**ape key.  This should give you the **grub** menu.

Then follow the instructions here [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

All the best

---

### Post by Patrick Lavelle on 2010-03-24
Yes I have tried the link you suggested but I am still not able to reset the password. Ubuntu was upgraded to 8.04 I think it said. After trying I rebooted the system it still asks for my Username and Password. While trying to receover my password i tried my daughters and my username and passwords and it came up and told me someting like bad bash and that was all. Don't know where to go from here. Like I said I have never used this Ubuntu system before and have been told it is a great system to use you just need to get your head around it. Maybe I should have not done the upgrade and things would be ok.

---

### Post by kamaji792 on 2010-03-24
Let's have one more go.

[list=1]
[*]Turn the computer off.
[*]Turn the computer on.
[*]Keep pressing and releasing the Escape key (Usually marked 'Esc') once a second.
[/list]

Do you get the **grub** menu?

It should look something like this:
```
 GNU GRUB version 0.95

Ubuntu, kernel 2.6.12-9-386
Ubuntu, kernel 2.6.12-9-386 (recovery mode)
Ubuntu, memtest86+

Use the up and down keys to select which entry is hightlighted.
Press enter to boot the selected OS. 'e' to edit the
command before booting. or 'c' for a command-line.
```

There is a image at the top of this thread:[http://ubuntuforums.org/showthread.php?t=925773](http://ubuntuforums.org/showthread.php?t=925773)

I can only think you were upgraded because support for v7 had finished.  The good news is if you can get into v8.04 it has support until about May 2011.

Good luck :D

---

### Post by Patrick Lavelle on 2010-03-24
Hi, I have done what you have suggested with the esc key and what I get coming up on a black screen is the following:
 
Ubuntu 8.04, kernel 2.6.24-16-generic
Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
Ubuntu 8.04, kernel 2.6.24-14-generic
Ubuntu 8.04, kernel 2.6.24-14-generic (recovery mode)
Ubuntu 8.04, memtest86+
 
Now from here is where I get lost as I don't get the screen that shows up on the link you have provided. So where do I go from here. Sorry to be such a pain with all this. I have tried the top two. the top one just reboots the system and I am still stuck with the dilema of having to enter the Username and Password without success. The second on from the top I did to try and reset the password without success thus having to reboot and still stuck with the Username and Password dilema. Now what do I try next. I don't know whether to try 3 and 4 from the top incase I do something wrong. I appreciate all the help you have given me so far. When I get the command line on the secon and 4th lines is root@ ACER:/# I enter the password that my daughter told to use and her username and the result I get is bash: password: command not found. I have even tried my password that was entered before the upgrade and my Name and I get the same thing. I just don't know where to go from here. All I can think is that the person who put the origanal Ubuntu program may have done something to prevent me from getting in although I was able to use the system on the earlier version of 7. something version. I hope this extra information I have supplied can give you more to work on to help me get through this problem.
 
Many thanks

---

### Post by kamaji792 on 2010-03-25
OK you should select the second item on the list:

**Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)**

I am running 9.10 and when I did it I got another menu from which I selected **Drop to root shell prompt** and then pressed Return.

That should give you a prompt like:
```
root@ACER:~#
```
To reset the password enter the following:
```
passwd <username>
```
The full dialogue should look something like:
```
root@ACER:~#passwd bill
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
root@ACER:~#
```
**Note** the spelling of the command and type a new password at the password prompts.

I then enter:
```
init 2
```

And this gives me a command prompt and I enter my user name and **new** password:
```
 ACER login: bill
Password:
```

Despite indications that this will give me a GUI I am still at the command prompt so I shut down with:
```
sudo halt
```
Entering the new password when prompted.

When it has shutdown restart you PC.

If you have done that and it is still not working let me know - I need some sleep now.

Good luck.

---

### Post by Patrick Lavelle on 2010-03-26
Hi, I have carried out the first two steps and bought up the Drop to root shell prompt and got the Code: [EMAIL="root@ACER:/"]root@ACER:/[/EMAIL]# I then entered passwd and my daughters username and I got the following screen:
Usage: passwd [options] [LOGIN]
 
Options:
-a, --all                                      report password status on all accounts
-d, --delete                                delete the password for the named account
-e, --expire                                force expire the password for the named account
-h, --help                                   display this help message and exit
-k, --keep-tokens                       change password only if expired
-i, --inactive INACTIVE                set password inactive after expiration to INACTIVE
-l --lock                                     lock the named account
-n --mindays MIN-DAYS              set number of days before password change to MIN-                                                DAYS
-q, --quiet                                  quiet mode
-r, --repository REPOSITORY       change password in REPOSITORY repository
-s, --status                                 report status on the named account
-u, --unlock                                unlock the named account
-w, warnings WARN-DAYS            set expiration warning days to WARN-DAYS
-x, --maxdays MAX-DAYS            set maximum number of days before      
                                                 password change to MAX-DAYs
[EMAIL="root@ACER:/"]root@ACER:/[/EMAIL]#
 
No I am not sure where to go from here. I have tried what it says at Usage: passwd [options] [LOGIN] but i get [EMAIL="root@ACER:/"]root@ACER:/[/EMAIL]# I am sorry that I am making you work hard on this problem but at least I have got further than I have before but don't know what to do from here. 
 
I don't come up with this dialogue as you have suggested but what I have typed above.:
Code:
---------
root@ACER:~#passwd bill
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
root@ACER:~#
I do hope that you are able to take me further with my situation.
 
Have a good nights sleep.
Your help is most appreciated.

---

### Post by kamaji792 on 2010-03-26
OK this is looking more promising.

Get to the point where you have the **root@ACER:~#** prompt and enter:
```
passwd -Sa | less
```
This command will show the status of all the passwords.  Piping it into **less** just lets you scroll up and down the list with the arrow keys.  Now you can check if the user name you are using still exists on the system.

I'm kind of guessing that the account does not exist any more.  If you do find the line with the account post it here.

Here is what mine looked like:
```
bill P 03/26/2010 0 99999 7 -1
```

When you are finished type 'q' to quit less and then
```
shutdown
```

All the best.

---

### Post by Patrick Lavelle on 2010-03-26
I have done the Code:
---------
passwd -Sa | less
---------
It showed me a list of different names, mine was there as:
paddy P  03/17/2010 0 99999 7 -1 it also shows the following:
lilbuuid L 03/17/2010 0 99999 7 -1
pulse L    03/17/2010 0 99999 7 -1
polkituser L 03/17/2010 0 99999 7 -1
 
I don't know what these mean but hope this hellps you to sort my mess out.
 
Thanks
Patrick Lavelle

---

### Post by kamaji792 on 2010-03-26
OK, when you are at the **root@ACER:~#** prompt you should be able to enter:
```
passwd paddy
```

(assuming **paddy** is your user name) Then you will have to enter a new password twice like:
```
root@ACER:~#**passwd paddy**
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
root@ACER:~#
```

Or does that not work?

---

### Post by Patrick Lavelle on 2010-03-26
My dear friend I wish to thank you so very much. After all the headaches I have had with this thing I did what you said and it was successful and now I am back on the internet. Thank you for working me through this problem. Could you tell me how often I should up grade my system and if I get into the same problem I will know what to do this time. I am so very grateful and don't know how to ever repay you.
 
Many thousands of thanks
Patrick Lavelle:KS

---

### Post by kamaji792 on 2010-03-27
Congratulation!

I am delighted you back on the internet.  I am not sure why you had the problem you had.  Even if it upgraded you from 7 to 8 I don't see why it lost your password.  It may be that it asked you for a new one and you did not notice the question.  I have never done a version upgrade.  I always do a fresh install.  Each version release is supported for 3 years with the exception of LTS (Long Term Support) versions which are supported for 3 years.  If you have been upgraded to 8.04 that will be supported until about April next year (because it was a LTS version).  9.10 is the current version but 10.04 LTS is due out in April.

I'm not sure what you best course of action is.  If you wanted to switch to v10 you would have to do a clean install. Which means backing up any data you want to retain, which could include e-mail's, e-mail addresses, browser favorites as well as other data files.  Or you could upgrade to v9 and then v10.  But for the moment you can just enjoy being able to use the system.

Here is a link to the page with the release cycle: [http://www.ubuntu.com/products/ubuntu/release-cycle](http://www.ubuntu.com/products/ubuntu/release-cycle)

I am glad we managed to sort the problem out.  I know a lot more about password recovery so I have learnt something in the process.

Any way all the best.

---

