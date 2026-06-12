---
title: "password protection?"
date: 2011-03-13
forum: General Help
---

### Post by netopalis45 on 2011-03-13
i would like a simple way of password protecting an application so that only i can open it. i would prefer not to have to make another user account to have to use sudo, gksudo, etc... to use it. is there some way of doing this?

---

### Post by Old *ix Geek on 2011-03-13
> **netopalis45 said:**
> i would like a simple way of password protecting an application so that only i can open it. i would prefer not to have to make another user account to have to use sudo, gksudo, etc... to use it. is there some way of doing this?Of course--this is Linux. :D A little more info would go a long way toward giving you a meaningful answer, though. What kind of program? A shell script? A commercial program? What's its name and where is it located? How is it normally invoked? From a menu, the command line, what?

---

### Post by netopalis45 on 2011-03-13
the program is mozilla seamonkey that i usually call using the applications menu. it is located in /usr/bin (at least according to whereis).

---

### Post by Old *ix Geek on 2011-03-14
> **netopalis45 said:**
> the program is mozilla seamonkey that i usually call using the applications menu. it is located in /usr/bin (at least according to whereis).You're talking about my browser! :D Okay, let me ask you this: Is your objective for you to be the only person who can run SeaMonkey, or do you specifically want to password protect it? I'm asking because there are different ways to accomplish the goal, depending on what the goal is. If you're looking to be the only person who can run SM--and don't actually want the hassle of being prompted for a password--we can go one way. If you actually want the program password protected, we'll go another way. Also, do you want to keep it so it's invoked from your apps menu, or would command line be better? What's your pleasure? :)

---

### Post by netopalis45 on 2011-03-14
i want to be the only one who can access it and dont mind having to put in a password. i would rather be able to access it through the apps menu but have no aversion to using the command line

---

### Post by Old *ix Geek on 2011-03-14
There are several ways you can go with this, and based on what you've said *I* would go with the easiest: Just change permissions on the SeaMonkey executable so you're the only user who can run it. If anyone else tries, it'll fail due to its permissions. Change ownership of the file to you, and change its permissions to 700.

If that's not a good choice for whatever reason (perhaps you keep your computer logged in as you and other people have access to it), then password protecting the file is better.

To do the latter, you're going to have to add some code to the script that launches SM. It's imperative that you make a backup copy of the file first...you know, just in case. :eek:

Post again with which way you want to go with this. I wrote and tested a password script but did it with Flock, not SeaMonkey, and if you're going with this method I want to be sure to test it for real before passing it on! :)

---

### Post by netopalis45 on 2011-03-14
my computer stays on all the time so it would be better if i could just password protect the file. i had attempted to change the permissions of the file but could not change ownership so your other method may not work.

---

### Post by bodhi.zazen on 2011-03-14
I advise you use encryption.

If you want a graphical front end, use cryptkeeper (it is in the repositories).

---

### Post by Old *ix Geek on 2011-03-14
> **netopalis45 said:**
> my computer stays on all the time so it would be better if i could just password protect the file. i had attempted to change the permissions of the file but could not change ownership so your other method may not work.You can change ownership via **sudo** or **su**. I'm assuming you're in the sudoers file and/or know root's password. If that's correct, just do this:

```
sudo chown your_user_name seamonkey_executable_file_name
sudo chmod 700 seamonkey_executable_file_name
```

Make sure you replace **your_user_name** with your user name, and **seamonkey_executable_file_name** with the name of the actual file you're changing. Look in your applications menu's entry for SeaMonkey to make sure you know which file you're going to change.

You mentioned that your **seamonkey** is in /usr/bin, but that's not the case for me. Of course, I install things in specific places, so the file I execute is /usr/local/seamonkey/seamonkey. Wherever your actual **seamonkey** file that gets launched from your menu is, go there and do the above commands to change its permissions.

If anything isn't clear, post again. I tend to assume everybody knows all the same stuff I do, and sometimes it's hard to make sure I've actually explained things so someone ELSE will get it! :D

---

### Post by netopalis45 on 2011-03-14
i have done that but it doesnt seem to have done anything other than change me to the owner. there is still no password required

---

### Post by Old *ix Geek on 2011-03-14
> **netopalis45 said:**
> i have done that but it doesnt seem to have done anything other than change me to the owner. there is still no password requiredRight. Log in as a different user and it won't launch. :)

But now that we know your computer is always logged in as you, the password method--or bodhi's encryption suggestion--would be a better choice.

Remember, BACK UP any file you're about to change and save it in a safe place! You've been warned. [-X

Please go to the directory containing the file **seamonkey** and type this:
```
file seamonkey
```

Does it yield something like **seamonkey: POSIX shell script text executable**?

If it does, please type the following and then paste the entire result here:
```
cat seamonkey
```

It should start out like this:
```
#!/bin/sh
#
# ***** BEGIN LICENSE BLOCK *****
# Version: MPL 1.1/GPL 2.0/LGPL 2.1
#
# The contents of this file are subject to the Mozilla Public License Version
# 1.1 (the "License"); you may not use this file except in compliance with
# the License. You may obtain a copy of the License at
# http://www.mozilla.org/MPL/
```

We're going to insert some code into this file.

Meanwhile, create a file in your home directory; I'm calling it smpwd but you can name this whatever you want--the less intuitive the better, like call it weather_report or something, so if someone manages to see the files in your home directory they won't be too tempted to look at that one. :D Create the file with whatever text editor you use (I use vi), and don't put anything in it but the password you want for this project; put that right at the beginning of the file and then save it and:
```
chmod 400 smpwd
```

---

### Post by netopalis45 on 2011-03-14
ok that is done. when i did the "file seamonkey" command it said that it is a symbolic link to another file but it doesnt give me the entire path so im not sure where it is yet. when i use the cat command it still comes up the way you said it would. eagerly awaiting the next step!

---

### Post by Krytarik on 2011-03-14
I may jump in here to push you in the right direction, as I'm following this thread.

If you are in the directory of the file to which the .desktop-file/launcher pointed to, run those command to get the link target:
```
ls -al SEAMONKEY_FILE
```

---

### Post by Old *ix Geek on 2011-03-15
> **netopalis45 said:**
> ok that is done. when i did the "file seamonkey" command it said that it is a symbolic link to another file but it doesnt give me the entire path so im not sure where it is yet. when i use the cat command it still comes up the way you said it would. eagerly awaiting the next step!Yeah, I figured the /usr/bin/seamonkey file wasn't the actual file. I mean SeaMonkey is installed somewhere else, and that's just a link to its installation directory's executable file.

We should be okay modifying the one you're looking at. I wanted to see your file's actual contents, but as long as you've got a good copy of it saved somewhere, we can plunge ahead.

With a text editor, edit the /usr/bin/seamonkey file. Go down past the initial block of commented lines (they start with #), being VERY CAREFUL not to modify anything. Don't add spaces, lines, characters or anything else! If you screw up, exit WITHOUT saving and start over.

Find the following lines:
```
#uncomment for debugging
#set -x
```

and add some blank lines after them. Then paste this in:
```
echo -n "Password: "

stty -echo
read password
stty echo

echo ""

goodpassword="$(cat $HOME/smpwd)"

if      [ "$password" = "$goodpassword" ]
then    continue
else    exit
fi
```

Okay, a couple of things. 1) This is NOT snooper proof! You're saving your password in a plain text file in your home directory. Anyone who can access your home directory can read its contents--I mean if they're logged in as you. If they're logged in as a different user they can't read it because of its permissions. Like I said before, I've called that file smpwd but you should name it something that doesn't draw attention to it. Then just make sure you adjust the code to reflect the actual name you've given the file. So, for example, if you decide to name the password file **birthday_cake**, this line:
```
goodpassword="$(cat $HOME/smpwd)"
```

needs to be changed to:
```
goodpassword="$(cat $HOME/birthday_cake)"
```

2) You can put your password file anywhere you want, as long as you're able to read from it. Again, modify the code to reflect its actual location and name.

3) I use KDE, but I'm assuming that you have an option available on your application menu to "run in terminal" or something similar. You need to go to SeaMonkey's menu entry and check that, otherwise you'll never see the password prompt.

I think that's it. Any problems, let me know!

---

### Post by netopalis45 on 2011-03-15
thank you. it worked wonders

---

### Post by Old *ix Geek on 2011-03-16
> **netopalis45 said:**
> thank you. it worked wondersYou're welcome. Glad it solved the problem. :)

---

