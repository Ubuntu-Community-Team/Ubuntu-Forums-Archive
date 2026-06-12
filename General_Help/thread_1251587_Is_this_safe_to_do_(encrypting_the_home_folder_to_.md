---
title: "Is this safe to do? (encrypting the home folder to gain privacy)"
date: 2009-08-27
forum: General Help
---

### Post by viking_maniac on 2009-08-27
[COLOR=black][FONT=Verdana]Hi, guys![/FONT][/COLOR]

[COLOR=black][FONT=Verdana]This is a sort of follow-up from [/FONT][/COLOR][COLOR=black][FONT=Verdana][[COLOR=#800080]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1201598")[/FONT][/COLOR][COLOR=black][FONT=Verdana] where I got angry about Ubuntu and its tendency to force history files to stay when I want to delete them.[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]I've tried several distributions now, but I eventually came back to Ubuntu again since this is the only one that actually I like. So here we go again ...[/FONT][/COLOR]


[COLOR=black][FONT=Verdana]I still want to eliminate the history, so in openSUSE I tried to encrypt the whole home folder for the user I wanted to protect. It actually worked--and this night I tried the same thing in Jaunty. That worked too! But I don't know if this setup is actually safe to use on a long term basis.[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]I installed TrueCrypt 6.02a on the default admin account and made an encrypted volume as in an encrypted file of 2GB.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Then I mounted that file and got this new folder: /media/truecrypt1/[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Then I added a new Desktop user and directed that user's home path to the /media/truecrypt1/ folder.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Then I switched user to my new encrypted user account and logged in. [/FONT][/COLOR]*[COLOR=gray][FONT=Verdana]Actually, at first the whole system crashed with an error message that said I had to make the new user home folder owned by the new user itself. I had to hard-boot and re-login as admin again. So I changed the /media/truecrypt1/ ownership to the new user and gave it full access just as with the admin account. But after that, it worked fine![/FONT][/COLOR]*
[COLOR=black][FONT=Verdana]Finally I got a new user with an encrypted home folder. And from what I can see, all history and traces are left in that folder. I just switch back to the main admin account and dismount the volume, and all history and traces are pretty much gone.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I can even log completely out from the main admin account before I login as the new user. TrueCrypt seems to still have its volumes mounted in the background--it's still there when I re-login as admin again.[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]So I'm wondering here if this is a safe and stabile solution for keeping my privacy at its best? I've also disabled the system logging service. I've never needed any logs in Windows, so I'm not going to start now! I hate logs! They just pile up.[/FONT][/COLOR]


[COLOR=black][FONT=Verdana]Thank you for any feedback![/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Greets! ;)[/FONT][/COLOR]

---

### Post by uylug on 2009-08-27
> **viking_maniac said:**
> [COLOR=black][FONT=Verdana]I've never needed any logs in Windows, so I'm not going to start now! I hate logs! They just pile up.[/FONT][/COLOR]


[COLOR=black][FONT=Verdana]Thank you for any feedback![/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Greets! ;)[/FONT][/COLOR]
Linux and Windows are completely different. Its dumb to ignore what is happening on the background because it often helps you fix problems.

If you want to remove your history (commands that you have run) then do this:
```

rm .bash_history
```

You may need to sudo it

```
sudo rm .bash_history
```

---

### Post by theozzlives on 2009-08-27
Believe it or not Windows writes log files to the disk all the time.

---

