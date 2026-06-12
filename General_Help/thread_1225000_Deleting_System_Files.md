---
title: "Deleting System Files"
date: 2009-07-28
forum: General Help
---

### Post by carolina on 2009-07-28
How can i permanently delete files that show in the File System icon ? These are files from a user that no longer has  access to this computer but whose files are still visible to other users via the Home folder ?

---

### Post by jocko on 2009-07-28
If you mean that the user account is still there, just not used anymore, just remove the user account and all associated files (after backing them up, if necessary):
```
sudo deluser --remove-all-files [COLOR=Red]USERNAME[/COLOR]
```That will delete the user [COLOR=Red]USERNAME[/COLOR] and all his/her files.

If you mean you have already removed the user account, but the users home directory is still there, just delete it ([COLOR=Black]**note: potentially harmful command follows, make sure you understand what it does and don't get any typos in the path**[/COLOR]):
```
sudo rm -rf /home/[COLOR=Red]USERNAME[/COLOR]
```That will delete the entire home directory of the user [COLOR=Red]USERNAME[/COLOR].

---

### Post by carolina on 2009-07-28
> **jocko said:**
> If you mean that the user account is still there, just not used anymore, just remove the user account and all associated files (after backing them up, if necessary):
```
sudo deluser --remove-all-files [COLOR=Red]USERNAME[/COLOR]
```That will delete the user [COLOR=Red]USERNAME[/COLOR] and all his/her files.

If you mean you have already removed the user account, but the users home directory is still there, just delete it ([COLOR=Black]**note: potentially harmful command follows, make sure you understand what it does and don't get any typos in the path**[/COLOR]):
```
sudo rm -rf /home/[COLOR=Red]USERNAME[/COLOR]
```That will delete the entire home directory of the user [COLOR=Red]USERNAME[/COLOR].

Jocko

The user account was removed from the user group . When i try the second code you gave and put in the deleted user name terminal asks for password . If i use the password that was used for that account terminal says " bash: password :command not found .

Thinking i did not understand what it is asking for i input the password i use from my primary account - same result . The deleted account was a second account i set up for myself as alan2 . My primary account is alan 1 .  This is what i see :   alan@alan-desktop:~$ 

So maybe i don't understand what it is asking for ?  I am a newbie to Linux .  :-)

Ps - If i were still using Windows this would not be an issue( even though i realize the data would still be on the hd )  as the account i deleted had banking info , etc in it . Our computer is used by my kids friends so i am sure you can see my point . :-)

---

### Post by nikhilk on 2009-07-28
> **carolina said:**
> Jocko

The user account was removed from the user group . When i try the second code you gave and put in the deleted user name terminal asks for password . If i use the password that was used for that account terminal says " bash: password :command not found .

Thinking i did not understand what it is asking for i input the password i use from my primary account - same result . The deleted account was a second account i set up for myself as alan2 . My primary account is alan 1 .  This is what i see :   alan@alan-desktop:~$ 

So maybe i don't understand what it is asking for ?  I am a newbie to Linux .  :-)

So the actual command you ran was
```
sudo rm -rf /home/alan2
``` right?

Yes, you are supposed to enter the password of the first user you created on your Ubuntu system (the primary user you have mentioned).

---

### Post by carolina on 2009-07-28
> **jocko said:**
> If you mean that the user account is still there, just not used anymore, just remove the user account and all associated files (after backing them up, if necessary):
```
sudo deluser --remove-all-files [COLOR=Red]USERNAME[/COLOR]
```That will delete the user [COLOR=Red]USERNAME[/COLOR] and all his/her files.

If you mean you have already removed the user account, but the users home directory is still there, just delete it ([COLOR=Black]**note: potentially harmful command follows, make sure you understand what it does and don't get any typos in the path**[/COLOR]):
```
sudo rm -rf /home/[COLOR=Red]USERNAME[/COLOR]
```That will delete the entire home directory of the user [COLOR=Red]USERNAME[/COLOR].

Jocko

The user account was removed from the user group . When i try the second code you gave and put in the deleted user name terminal asks for password . If i use the password that was used for that account terminal says " bash: password :command not found .

Thinking i did not understand what it is asking for i input the password i use from my primary account - same result . The deleted account was a second account i set up for myself as alan2 . My primary account is alan 1 .  This is what i see :   alan@alan-desktop:~$ 

So maybe i don't understand what it is asking for ?  I am a newbie to Linux .  :-)

---

### Post by carolina on 2009-07-28
That is the command i ran and when i input my primary password this is what i get :     alan@alan-desktop:~$

I don't understand what the terminal is saying or perhaps asking additionally for ?  :-)

---

### Post by nikhilk on 2009-07-28
> **carolina said:**
> That is the command i ran and when i input my primary password this is what i get :     alan@alan-desktop:~$

I don't understand what the terminal is saying or perhaps asking additionally for ?  :-)

So after executing the command you return back to the prompt? In that case the command was successfully executed.

See if the directory is still there
```
ls /home
```

---

### Post by nothingspecial on 2009-07-28
If the terminal doesn`t say anything to you it is because it has done whatever you told it to do.

Type ```
ls /home/
```

Is alan2 in there? If not you have sucessfully deleted all his files.

---

### Post by carolina on 2009-07-28
> **nothingspecial said:**
> If the terminal doesn`t say anything to you it is because it has done whatever you told it to do.

Type ```
ls /home/
```Is alan2 in there? If not you have sucessfully deleted all his files.



The files are still there . Terminal in fact lists every user account .  :-) Would a reboot be required ?

---

### Post by nothingspecial on 2009-07-28
From your primary account (alan1) type ```
sudo rm -rfv /home/alan2
```

Then type alan1`s password.

[COLOR="Red"][SIZE="3"]Do not type the command wrong![/SIZE][/COLOR]

The v flag will show you what is being deleted in the terminal.

Or if you prefer type

```
gksudo nautilus
```

Click file system (in the right hand bar) then click home and delete alan2 from there.

Do not delete home, that really will cock things up. Just the directory alan2. Don`t delete alan1 by miistake.

---

### Post by carolina on 2009-07-28
> **nothingspecial said:**
> From your primary account (alan1) type ```
sudo rm -rfv /home/alan2
```

Then type alan1`s password.

[COLOR="Red"][SIZE="3"]Do not type the command wrong![/SIZE][/COLOR]

The v flag will show you what is being deleted in the terminal.

Or if you prefer type

```
gksudo nautilus
```

Click file system (in the right hand bar) then click home and delete alan2 from there.

Do not delete home, that really will cock things up. Just the directory alan2. Don`t delete alan1 by miistake.
Thanks Nothing Special but i think you are something special  as that did the trick .  :-) 

Problem Solved

---

