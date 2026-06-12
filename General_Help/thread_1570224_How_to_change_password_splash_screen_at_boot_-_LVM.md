---
title: "How to change password splash screen at boot - LVM Encrypted Kubuntu"
date: 2010-09-07
forum: General Help
---

### Post by Alexander D. Gray on 2010-09-07
Hello everyone,

So I recently installed kubuntu 10.04 on my laptop, using the alternate cd and setting up the LVM encryption.

Now when I boot up the first thing I'll see after some general loading is a splash screen that says kubuntu, lets me know my drive is encrypted, and provides me with a box to enter my password.

On my non encrypted ubuntu set-up I've changed it to a text based login that has some flavour text, thereby not indicating the name of my operating system so readily.

I was wondering if I can change this spash screen to more of a console-looking screen, and thus remove the obvious references to kubuntu and encryption. Best case scenario would to simply have a black screen that says something along the lines of 'enter passphrase'.

Given that you can change a splash login screen to text based, I'd reckon you can do this too, but I'm not sure which file I should edit, and am not quite sure if I'm using the correct vocabulary when asking about it. I don't want to botch anything as screwing up encrypted drives isn't very fun.

In short, I would like to change the splash screen promting you for the password to decrypt your harddrive before booting kubuntu 10.04. Anyone know how?

Thanks in advance!

---

### Post by Alexander D. Gray on 2010-09-08
So after a bit of tinkering around I found that if you change /etc/default/grub and edit the line "quiet splash" to "quiet text" you'll get the desired result of a text based login and text based encryption password prompt.

Now the first thing I see when I boot is a line that says my encrypted volume, followed by a line that asks for my password. Oddly enough though, each time you type a letter for this password, the line goes down one line and the line describing the encrypted file repeats. Like this

yaddayaddaencryptedpartition
                      enterpassword: _

Will become

yaddayaddaencryptedpartition
yaddayaddaencryptedpartition
yaddayaddaencryptedpartition
                      enterpasword:***

After three letters, repeating itself for all the letters of the password.

I was wondering if anyone know about this behaviour, and in particular if it could be turned off. Also, is it possible to change the line refering to my encryption? I'd like to change it to something that doesn't refer to my system being encrypted at all.

Thanks!

---

### Post by Alexander D. Gray on 2010-09-16
I'm still trying to troubleshoot this issue, but haven't really had much success in figuring out what controls this particular behaviour.

Would anyone be able to point me in the direction of what files control the prompt for the encryption password in a kubuntu 10.04 setup?

Thanks for the help.

---

