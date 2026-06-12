---
title: "Cant get into admin options"
date: 2006-04-13
forum: General Help
---

### Post by Striker_XF35 on 2006-04-13
Hello, I just installed ubuntu as a second OS (1st is Windows XP which im on now) and i cant get into the administrative options, in other words, when i click on network setup it asks for my password and when i give it i then must wait a second and it closes.
same with most other options, (i can edit screen res. i know)
anyone know what causes this?
Thanks,
Striker

---

### Post by 5-HT on 2006-04-13
You didn't happen to do an 'expert install' did you?
This exact same question is being posted almost daily now, and a little searching can go a long way.

If you did do an expert install, the following will describe what is going on and how you can fix it.
If you did not do an expert install, this post may still apply.

The GUI adminstration tools in Ubuntu utilize sudo/gksudo to escalate user privileges.

The expert install does not add the user you created during the install to the 'sudoers' file .
This file is what determines who can/can't use sudo, as well as what they can/can't use it for.

Even if you did not perform the expert install, most likely your sudoers file is the cause of your problems.

Here is a great post from Mustard that describes how you can add your user to the sudoers file.
[http://ubuntuforums.org/showpost.php...70&postcount=4]("http://ubuntuforums.org/showpost.php?p=860170&postcount=4") 

(Original thread: [http://ubuntuforums.org/showthread.p...hlight=sudoers]("http://ubuntuforums.org/showthread.php?t=150021&highlight=sudoers"))

You basically need to boot into single user mode so you can become root, and then add your user to the sudoers file. Mustard's post is a great walkthrough of the process.

Hope this helps.

---

