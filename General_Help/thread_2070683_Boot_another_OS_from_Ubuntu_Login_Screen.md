---
title: "Boot another OS from Ubuntu Login Screen"
date: 2012-10-13
forum: General Help
---

### Post by java_java_and_more_java on 2012-10-13
I would like to be able to boot into other OSes by selecting an option from the login screen of Ubuntu i.e. 'Boot into Windows' from the login screen which would reboot the PC into Windows. On the next boot it should login back into Ubuntu again.

I read a tutorial somewhere on the net explaining how to do this so I know it's possible but I can't find it now!

Thanks.

---

### Post by cipherboy_loc on 2012-10-13
In my opion, it is probably more work than it is worth, why not just select Windows on the grub menu? If you aren't seeing the menu or you don't have enough time to select a different operating system, then you can search the forum for information about modifying grub config.

However, for what you want to do to work, you need to modify a grub config file to set the default option to windows, run update-grub (which will take a few seconds or longer to complete) to regenerate the grub menu file with the new default option, then issue a reboot request. However, after booting and doing stuff in Windows, it will continue to default to windows until you select Linux in the grub menu and change your grub config file, and rerun update-grub. 

In other words, unless I am missing a kep option in the grub config, it is more work than what it is worth.


Thanks,
Cipherboy

---

### Post by Cheesemill on 2012-10-13
> **cipherboy_loc said:**
> However, for what you want to do to work, you need to modify a grub config file to set the default option to windows, run update-grub (which will take a few seconds or longer to complete) to regenerate the grub menu file with the new default option, then issue a reboot request. However, after booting and doing stuff in Windows, it will continue to default to windows until you select Linux in the grub menu and change your grub config file, and rerun update-grub. 

In other words, unless I am missing a kep option in the grub config, it is more work than what it is worth.
Take a look a t the grub-reboot command, you can use it to tell grub which OS to use for the next boot only.
I'm unsure on how you would modify LightDM to give you this functionality though.

---

### Post by cipherboy_loc on 2012-10-13
Thank you, cheesemill.

[http://askubuntu.com/questions/54507/add-a-new-custom-session](http://askubuntu.com/questions/54507/add-a-new-custom-session)

More or less, create a custom session entry, point it at a script (probably in /usr/local/bin) and have that run grub-reboot (see last post in this thread [http://ubuntuforums.org/showthread.php?t=1530022](http://ubuntuforums.org/showthread.php?t=1530022)).

Make sure you check for root, and edit out the sudo command in your script, and you should be good. If you need more help, post back here with what you have thus far.


Thanks,
Cipherboy

---

