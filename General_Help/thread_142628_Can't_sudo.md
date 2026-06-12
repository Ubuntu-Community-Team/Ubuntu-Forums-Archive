---
title: "Can't sudo"
date: 2006-03-10
forum: General Help
---

### Post by Volmarias on 2006-03-10
I'm having some trouble with my install.

I've created one user, during install. I can't use anything inside of the Administrator folders. Why? I can't sudo.

I **CAN** su.

I've su'd and then set the password for root.

I **CAN** press ctrl-alt-f1 and login as root. the password works.

Whenever I try to do anything with sudo or gksudo, my password is denied.

I **CAN'T** use sudo, therefor
I **CAN'T** just click on anything in the administrator folder.

However, using su, I can log in as root and perform the commands from the command line. I've looked in user-admin at myself.

Here is a screenshot of the user's administration. Note the number of users.
[http://volmarias.semimajor.net/images/userscreenshot1.png](http://volmarias.semimajor.net/images/userscreenshot1.png)

Here is a screenshot of my user priviledges. Note what is checked.
[http://volmarias.semimajor.net/images/userscreenshot2.png](http://volmarias.semimajor.net/images/userscreenshot2.png)

I asked on IRC, and an option was mentioned that I don't seem to have.

Basically, I think I'd be fine if someone told me what to put in my sudoers file, but otherwise, remember, when giving instructions, I CAN'T CLICK ANYTHING IN THE ADMINISTRATORS FOLDER so you'll have to give me the name of the program to run from the command line.

Thanks in advance for the help, sorry to be pissy but I'm surprised that this didn't seem to happen for anyone else.

---

### Post by bluevoodoo1 on 2006-03-10
Hmmm... I had a problem like this before, let me see if I can remember how I solved it...  if you login with root can you get to /etc/sudoers (nano /etc/sudoers) and make sure your login looks like this... 

bluevoodoo1   ALL=(ALL) ALL

(replace bluevoodoo1 with your login of course)

Ctrl+o to save then Ctrl+x to exit. 


this link might help too... [https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo](https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo)

EDIT: typo

---

### Post by taurus on 2006-03-10
What groups do you belong to?  You can either look at /etc/group to see if your login name is at the end of adm or at the prompt, type
```

id

```

---

### Post by Volmarias on 2006-03-12
[QUOTE=bluevoodoo1]Hmmm... I had a problem like this before, let me see if I can remember how I solved it...  if you login with root can you get to /etc/sudoers (nano /etc/sudoers) and make sure your login looks like this... 

bluevoodoo1   ALL=(ALL) ALL

(replace bluevoodoo1 with your login of course)

Ctrl+o to save then Ctrl+x to exit. 


this link might help too... [https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo](https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo)

EDIT: typo[/QUOTE]

I tried that. I had

volmarias ALL=(ALL) ALL

just like root had it. No dice.

Anyway, I changed the sudoers file, couldn't get it to work, changed it back. Thought maybe I had to log out and log in. Logged out. Attempted to log in.

Gray screen, unending.

After 5 minutes of waiting, I rebooted, tried again.

Same deal. I could log in, but couldn't get past the gray screen.

Said f*ck it, stuck the Ubuntu CD in, and reinstalled.

Foolishly set one of the monitor resolutions to 1600x1200 (it really WOULD be nice if you could specify which would be chosen by default, or if there was a warning that the highest would be chosen automatically).

Restarted, as per instructions.

"Monitor out of range"

%_)!*(&^%!)&@^$%!@)%&*(!^_!()@*$!@(#*&!

Stuck the CD back in, pressed reset.

**BEEP** ...... **BEEP** ...... **BEEP** ....

!()*&%!)@(*&^!&%!%()_&*!@$)!(*&%(*^@!$

Turned off the machine, went to bed with the girlfriend. Haven't touched it since.

I'll try playing with sudoers again (IF I can even get it to start). Has anyone considered putting into the troubleshooting section of the manual "What to do if you can't use anything in the administrators section because for some reason you're not a sudoer and every single f*cking instruction assumes that you are" ?

---

### Post by NeghVar on 2006-03-12
Quick question. You say you set your root password. When you go to use Sudo and it asks for your password, are you giving what you set your Root password as or what your login password is. What it wants is your login password.

I know it may seem like a stupid question, but I've learned that with most problems its just some silly mistake.

---

### Post by Lord Illidan on 2006-03-12
Can you boot in failsafe, and remove the offending values out of /etc/X11/xorg.conf

---

### Post by knalle on 2006-03-12
[QUOTE=bluevoodoo1]if you login with root can you get to /etc/sudoers (nano /etc/sudoers) and make sure your login looks like this... 
[/QUOTE]

no no no, there is only one way to edit the sudoers list and thats with **visudo** if you open the file in nano you are not allowed to save it

---

### Post by Volmarias on 2006-03-13
[QUOTE=NeghVar]Quick question. You say you set your root password. When you go to use Sudo and it asks for your password, are you giving what you set your Root password as or what your login password is. What it wants is your login password.

I know it may seem like a stupid question, but I've learned that with most problems its just some silly mistake.[/QUOTE]

I knew I should have mentioned it above, because everyone asks it. But yes.

In this case, the root password was actually the same as my user's password. I knew the password, could login as root via a different login prompt (ctrl-alt-f1), etc. The problem I think was that I wasn't in the sudoers file for some reason.

Anyway, I've taken the brute force approach that shows my years of windows use, and reformatted/reinstalled until the bleeping distro took. The machine is finally up and running, with the default user account being given sudo priviledges (hooray!), and it's merrily purring away in the next room.

Thanks for the help and the suggestions, everyone!

---

### Post by bluevoodoo1 on 2006-03-13
[QUOTE=knalle]no no no, there is only one way to edit the sudoers list and thats with **visudo** if you open the file in nano you are not allowed to save it[/QUOTE]

Well, I just tried it my mehotd twice and it works as well. Ctrl+Alt+F1. Login as root. then nano /etc/sudoers (edit to your liking) Ctrl-o to save Ctrl-x to exit. Plus Volmarias said this... 

> I CAN press ctrl-alt-f1 and login as root. the password works. 
so it should have worked. But visudo should have worked too. 

But anyway, the problem seems to be have been resolved.

EDIT: The /etc/sudoers file claims it "MUST" be edited with visudo? Why? Why not the method I tried? (Even though it works) Security issue?

EDIT 2: To answer my own question... From the wiki "To edit that file, you must use visudo as it will error check the file before exiting. "

---

