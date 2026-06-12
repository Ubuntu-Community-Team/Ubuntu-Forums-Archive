---
title: "Bash (?) script for creating a shortcut for a Terminal command"
date: 2011-01-09
forum: General Help
---

### Post by nrabett on 2011-01-09
In my home LAN, I let the router assign ip-addresses according to the MAC address of a device. This creates a problem for one of my laptops, which I use both with a wireless and wired connection. Instead of creating separate port forwards etc. for both MAC addresses, I prefer to change the MAC of eth0 (wired) with Macchanger by opening a Terminal and typing:

sudo macchanger -m (new address) eht0

This works fine, but I would like to make a short program so that I can create a desktop shortcut which executes this command - ideally so that I don't have to enter my password every time. 

I know that I can create a Bash script (hopefully this is the correct word) in Gedit, and make it executable, but I do not understand what to write in the document.

---

### Post by Crusty Old Fart on 2011-01-10
First, let's assume you have created an extra user account for "batman" with special privileges as described later.

Then, the following short script should work as long as you edit the text shown in blue with the appropriate replacements.
```

#!/bin/bash
sudo -u [COLOR=Blue]**batman**[/COLOR] sudo macchanger -m [COLOR=Blue]**(new address)**[/COLOR] eth0
exit 0

```Here's how to create the special "batman" account. You can use any name you want for "batman" and your username for the user named Trolen, for whom the following post was originally written.
> **Crusty Old Fart said:**
> Okay...I've had enough of all this  Ubuntu Nanny B.S. I'm going to tell Trolen, and everybody else who wants  a computer instead of a frappin' babysitter, a safe way to remove the  password verification annoyance.  With any luck, I won't make folks who  are afraid that Trolen's system will get taken over and attack all  creation any more paranoid than they already are.

The idea here is to create a user with special rights, more powerful  than an administrator, but not as powerful as root. We'll name him:  batman for this example. We'll make him an administrator. We'll give him  special rights in the sudoers file, And finally, assuming that Trolen's  userid is: trolen, we'll set him up in the sudoers file to be able to  run commands as batman, then we'll downgrade trolen to a desktop user.

So here we go, by the numbers (Note: the click sequences shown below work for Lucid):

[LIST=1]
[*]_Create user: batman:_  System > Administration > Users and Groups > Add > Name:  Batman > Short Name: batman > OK > New password: whatever >  Confirmation: whatever > OK <--Don't close this window yet, Follow  the instructions in step 2.
[*]_Make Batman an adminstrator:_  To the right of the text "Account type:", click: Change > click the  radio button to the left of: Administrator > OK > Close.
[*]_Open the sudoers file for editing with the following command:_```
sudo visudo
```
[*]_Add the following lines to the bottom of the sudoers file:_```
# Allow batman to run any commands anywhere without a password
batman       ALL=(ALL)       NOPASSWD: ALL

# Allow trolen to run any commands as user: batman without a password
trolen       ALL=(batman)       NOPASSWD: ALL
```
[*]_Save the sudoers file and exit the editor._
[*]_Downgrade user: trolen to a desktop user (optional, but recommended):_  System > Administration > Users and Groups > To the right of  the text "Account type:", click: Change > click the radio button to  the left of: Desktop user > OK > Close.
[/LIST]
That's it. The  heavy lifting is over. The adminstrator account is now: batman, and  user: trolen has been downgraded to a desktop user, which is safer than  he may have been running as an adminstrator (default system setup for  one user)

From this point forward, anytime trolen wants to run root privileges,  instead of entering something like:```
sudo cat /etc/sudoers
```and  then being pestered to give the babysitter a password, he can  use:```
sudo -u batman sudo cat /etc/sudoers
``` ...and the  babysitter will leave him alone.

Furthermore, and THIS is my favorite part, trolen can write scripts with  sudo commands in them without the scripts pestering him for a password  when it runs. It's done the same way as what is done on the command  line. For example:
This will pester trolen for a password:```
#/bin/bash
sudo cat /etc/sudoers
exit 0

```Wheras the following script will just flat out RUN!:
```

#!/bin/bash
sudo -u batman sudo cat /etc/sudoers
exit 0

```Now, [COLOR=Red]**as long as Trolen always logs on as: trolen, and never: batman**[/COLOR], boo's computer, and everybody else's will be protected :cool:

[SIZE=2]**[COLOR=Red]WARNING: With the user accounts  configured as described above, running sessions while logged in as  "batman" puts the system at serious risk and should NEVER be done.[/COLOR]**[/SIZE]**[COLOR=Red] [COLOR=Blue]<--Edit: new warning (Hat tip to boo for the suggestion).[/COLOR][/COLOR]**

In my crusty opinion, it's a helluva lot better to tell a noob how to do   something, and do it right, than to hide it from him, and have him  mess  things up by experimenting without a clue.
So...there. I hope everybody is happy.

Any questions?,

Crusty

I'd be happy to answer any questions you may have if this post isn't clear.

Good luck,

Crusty

---

### Post by nrabett on 2011-01-11
Thanks! I'll name the account Batman.

---

### Post by Crusty Old Fart on 2011-01-11
> **nrabett said:**
> Thanks! I'll name the account Batman.
You're mighty welcome.
We had a typo: eht0 should have been: eth0. I've gone back and edited my post.
If you have any trouble with it, feel free to ask.

All the best,

Crusty

---

