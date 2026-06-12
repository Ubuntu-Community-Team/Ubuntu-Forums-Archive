---
title: "Im not in the sudoers file?"
date: 2006-04-18
forum: General Help
---

### Post by evillawngnome on 2006-04-18
Yeah, im not real sure how i effed this up, but now i cant sudo. How do i fix this?

---

### Post by user1397 on 2006-04-18
[quote=evillawngnome]Yeah, im not real sure how i effed this up, but now i cant sudo. How do i fix this?[/quote]
What exactly does it say when you type in "sudo" in a terminal?
Also, what did you do that might have caused this?

---

### Post by evillawngnome on 2006-04-18
administrator@STLLNDEV:~$ sudo su
sendmail: fatal: open /etc/postfix/main.cf: No such file or directory
administrator is not in the sudoers file.  This incident will be reported.

The sendmail fail doesnt bother me; i know what thats about.

The last command i did involved the CHGRP command. I think it was
CHGRP -G webadmin administrator

---

### Post by user1397 on 2006-04-18
[quote=evillawngnome]administrator@STLLNDEV:~$ sudo su
sendmail: fatal: open /etc/postfix/main.cf: No such file or directory
administrator is not in the sudoers file.  This incident will be reported.

The sendmail fail doesnt bother me; i know what thats about.

The last command i did involved the CHGRP command. I think it was
CHGRP -G webadmin administrator[/quote]
In ubuntu you don't use sudo su, just sudo.  That should work.

---

### Post by evillawngnome on 2006-04-18
well i cant sudo ANYTHING anymore.

administrator@STLLNDEV:~$ reboot
reboot: must be superuser.
administrator@STLLNDEV:~$ sudo reboot
administrator is not in the sudoers file.  This incident will be reported.
administrator@STLLNDEV:~$ sendmail: fatal: open /etc/postfix/main.cf: No such file or directory

---

### Post by user1397 on 2006-04-18
Were you trying to open the sudoers file in /etc/sudoers?
the command for this is "sudo gedit /etc/sudoers"

---

### Post by evillawngnome on 2006-04-18
administrator@STLLNDEV:~$ sudo pico /etc/sudoers
sendmail: fatal: open /etc/postfix/main.cf: No such file or directory
administrator is not in the sudoers file.  This incident will be reported.

I havent touched the sudoers file. I have no idea how i got this sudo thing hosed.

---

### Post by user1397 on 2006-04-18
wow very weird.
well i think there are threads in the forums similar to your case.
just search for "sudo doesn't work" and similar things

---

### Post by evillawngnome on 2006-04-18
The last command i did involved the CHGRP command. I think it was
CHGRP -G webadmin administrator .

What i was trying to do was make it so that my user account, administrator, had read/write access to /var/www. I successfully changed the group ownership of that directory to webadmin, and i just needed to add myself to that group.

---

### Post by 5-HT on 2006-04-18
*EDIT:
I was writing this at the time you posted. I'm not sure what you've done with the groups, but if you did a default install then your initial user is a member of either the adm or admin groups. Being a member of those groups is what allows sudo rights. 
If you are no longer part of one of these groups, adding yourself to one of them via recovery mode should fix the problem. 
To see whether you need to add yourself to adm or admin groups, look at the bottom of the sudoers file and there should be mention to one of them.
----------------------------------------------------------

[quote=evillawngnome]Yeah, im not real sure how i effed this up, but now i cant sudo. How do i fix this?[/quote] 
If you boot up into recovery mode you can add your user to the sudoers file.
At the GRUB screen, pressing 'esc' will give you an option to boot into recovery mode.

To add youself to the sudoers file, run:
```
visudo
``` 
Depending on whether you are part of the adm or admin groups, you can give yourself sudo rights by adding either: ```

%admin          ALL=(ALL) ALL

OR

%adm            ALL=(ALL) ALL 
``` 
Alternatively, you could just add your user directly:
```
username     ALL=(ALL) ALL
``` 
Hope that helps.

---

### Post by evillawngnome on 2006-04-18
Awesome! Im going to reboot here into recovery mode, and ill give it a shot. Ill let you know how i come out. THanks!

EDIT:

Whats the proper way to add myself to a group? I think this is where i went wrong.

---

### Post by evillawngnome on 2006-04-18
AHA! I found the problem: When i did:
chgrp **-G** webadmin administrator

the capital G expects a list of groups, and i only fed it one, therefore i wiped out all my old groups. Does anyone have a list of the default groups for the initial user?

---

### Post by 5-HT on 2006-04-18
[quote=evillawngnome]AHA! I found the problem: When i did:
chgrp **-G** webadmin administrator

the capital G expects a list of groups, and i only fed it one, therefore i wiped out all my old groups. Does anyone have a list of the default groups for the initial user?[/quote] 
I'm not familiar with chgrp, but looking at the man page I could not see any mention to the 'G' option. Unless 'G' has a function like you described that is undocumented, you changed the group associated with 'administrator' (file) to be changed to the group 'webadmin'.

If this is true it shouldn't have really caused either the admin/adm groups to be removed, and putting yourself back into either adm or admin* (for whatever reason you were removed from them) should clear it up.


*My previous post described a way to find out if you need to be added to either adm or admin (it depends one which version you initially installed).

[quote=evillawngnome]Whats the proper way to add myself to a group? I think this is where i went wrong. [/quote] 
[LEFT]Syntax to add an existing user to an existing group: ```
 adduser *user group *
```
In your case, this would have to be done in recovery mode.
[/LEFT]

---

### Post by 5-HT on 2006-04-18
[quote=erik1397]Were you trying to open the sudoers file in /etc/sudoers?
the command for this is "sudo gedit /etc/sudoers"[/quote] 
Just as an aside to avoid possible problems, it is not recommended (and may not even be allowed) to edit the sudoers file with anything but 'visudo'.

Why? visudo will make a backup copy of the sudoers file while editing, and will check changes for errors. If you circumvent this, it could render the file corrupt and useless.

You could edit the file by visudo using your preferred editor by setting the EDITOR env var prior to invoking visudo. 
For example, if you'd like to user gedit:
```
 export EDITOR=gedit && visudo 
``` 
Just a precaution, but better safe than sorry.

---

