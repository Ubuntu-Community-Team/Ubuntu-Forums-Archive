---
title: "just installed, can't even log in"
date: 2006-05-11
forum: General Help
---

### Post by fbb on 2006-05-11
Hi.  My experience with Linux is just fooling around with the Ubuntu live CD a few times.  I got on the web and got my printer to work with it, but that's about it.

Now I just cleared off a partition and installed Ubuntu 5.10.  I have to admit I guessed on a lot of the installation option questions.  (For the record I don't think those questions should be asked if you want to make Ubuntu more accessible to newbies.)

The main problem I had was when it asked for a username and password.  I kept entering the same ones over and over again, and it was like it was caught in an infinite loop.  There would be a little error message at the bottom each time, after I retyped my password, and then it would start over and ask to create a user account over again.  I finally cancelled and proceeded with the installation.  At one point I did enter a root account password.

Ok, so it finally finishes and it's time to log in, and lo and behold, I can't login because, I guess, it never successfully made an account!  However, down in the lower right, by the time, is the username I entered over and over again.  However, the password doesn't work.  I tried the root password (along with username "root"), and that didn't work either.

Any clue what could have caused this?  I was really looking forward to using Ubuntu, but so far it looks like it's still in diapers and doesn't really know what it's doing yet.

---

### Post by Dr. Nick on 2006-05-11
:( It wasnt a infinite loop. I remember almost making that same mistake. What its doing is creating multiplle accounts. Once you make one their should be a way to continue wothout making another, Its been awhile since I did this so I forgot the exact method. Maybe reinstalling would be best. If you have questions on a part feel free to ask for help.

You will be glad to know that the new dapper live cd will install to the hard drive within a full gui and its dialogs are very newbie friendly.

---

### Post by fbb on 2006-05-11
[QUOTE=Dr. Nick]:( Once you make one their should be a way to continue wothout making another, Its been awhile since I did this so I forgot the exact method. Maybe reinstalling would be best. [/QUOTE]

The only 2 options at the bottom were OK and Cancel.  I finally hit Cancel after entering the same username and password at least 5 times.  I thought the same thing you said, that it was creating multiple accounts and would finally end, but after a while I found it harder and harder to believe.

I would be happy to reinstall, but I'm worried that the same thing will happen again if I do things the same way.

[QUOTE=Dr. Nick]You will be glad to know that the new dapper live cd will install to the hard drive within a full gui and its dialogs are very newbie friendly.[/QUOTE]

That is good.  I was thinking it should at least have a way to navigate back and change things, or come up for air and see where you are (and if it's making multiple accounts, first of all why is it doing so, and second, why didn't it tell me this?

But glad to know things are being ironed out.  I can't wait to ditch Windows.

---

### Post by Dr. Nick on 2006-05-11
Not sure what is going on, Dont know if having multiple accounts with the same name messes it up or not.

Root isnt enabled in ubuntu by default. Also the username shouldnt appear on the login screen. The name in the bottom corner is the hostname, not the user name. A reinstall may be best if it doesnt take to long. just make one account and hit cancel at the next one. It probably could be a little clearer on exactly what it is doing. Their is also no root password set in the install, when root pass is needed it will be the password for the FIRST user you created. So if you want multiple accounts make yours first

---

