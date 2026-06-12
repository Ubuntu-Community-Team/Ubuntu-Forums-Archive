---
title: "What's the best way to hide a folder in 8.04?"
date: 2009-10-20
forum: General Help
---

### Post by deBALZAC on 2009-10-20
I only 1 user account and the best way I found to avoid other user (my gf) to browse a folder X is by password-encrypting it with WinRar (Wine).

I bet there's a best way I could use so my gf would not be able to browse this directory, so that's why I created this thread.

I'd like alternative solutions for this. Maybe there is a way I could set the folder to ask for password each time it's accessed without the need of creating another user account?

---

### Post by nothingspecial on 2009-10-20
Does your gf know your password.

If not, just put it in the root directory and change the owner to root and make the permissions 700.

---

### Post by pedro_orange on 2009-10-20
Chmod them so that only root can open it.

---

### Post by kimberlite on 2009-10-20
You can encrypt folders as well. There is a video how-to on CryptKeeper: [http://www.youtube.com/user/gotbletu#p/u/85/5zLCjxg7p-U](http://www.youtube.com/user/gotbletu#p/u/85/5zLCjxg7p-U)

---

### Post by Primefalcon on 2009-10-20
> **kimberlite said:**
> You can encrypt folders as well. There is a video how-to on CryptKeeper: [http://www.youtube.com/user/gotbletu#p/u/85/5zLCjxg7p-U](http://www.youtube.com/user/gotbletu#p/u/85/5zLCjxg7p-U)
Truecrypt is probably easier to use permissions are never a sure fireway to hide anything especially if she knows how to use a livedfisk or has access to sudo

---

### Post by dj-toonz on 2009-10-20
if the folder is in your home folder that you want to hide, you can do it with just using gedit,

make a text file called .hidden (no extension)

enter the folders that u want to hide in the file

i.e on mine I've got

Desktop
Dropbox
Templates
Public

and then save & refresh with f5 & the folders have vanished (invisible to the naked eye) to see them again, just goto view, show hidden files & folders

That's what I do as if it's invisible my gf wouldn't know what was in the folder or even bother (if the folder was passworded, she would keep going on about why it was passworded for weeks or even delete the folder

---

### Post by theozzlives on 2009-10-20
> **deBALZAC said:**
> I only 1 user account and the best way I found to avoid other user (my gf) to browse a folder X is by password-encrypting it with WinRar (Wine).

I bet there's a best way I could use so my gf would not be able to browse this directory, so that's why I created this thread.

I'd like alternative solutions for this. Maybe there is a way I could set the folder to ask for password each time it's accessed without the need of creating another user account?

Give your GF her own account with Desktop User privileges, and change your password. She won't be able to access your home folder. Put your porn in the /root as mentioned above.

---

### Post by stinkeye on 2009-10-20
> **kimberlite said:**
> You can encrypt folders as well. There is a video how-to on CryptKeeper: [http://www.youtube.com/user/gotbletu#p/u/85/5zLCjxg7p-U](http://www.youtube.com/user/gotbletu#p/u/85/5zLCjxg7p-U)
+1 for cryptkeeper
simple to use

---

### Post by StuartN on 2009-10-20
> **deBALZAC said:**
> a best way I could use so my gf would not be able to browse this directory

Develop a more trusting relationship with your partner?

---

### Post by kpholmes on 2009-10-20
just put a period "." before the name and it will become hidden ie. 

```
.secret
```

and use 

```
ls -a
```

to find it.

unless the other users dont know that command, or right click in the directory on where it resides and selects to show hidden files, then it will be completely invisible. 

or just but it on a ".hidden" folder on a pen drive with some decoy documents.

---

### Post by Dr_Bobby on 2009-10-20
Hiding files/folders is not security!  Truecrypt is the best way to go if you want to keep sensitive information (p0rn in your case) secret.

---

### Post by nothingspecial on 2009-10-20
I know this is supposed to be a tech support forum, but........

...... a little bit of personal advice.

Women know what men are like. If I had a directory full of what we all think yours is full of and my wife knew about it, she`d just roll her eyes and stay out of it.

If she found it, she`d be a bit cross.

If she stumbled upon it after I`d hidden/encrypted/passworded....etc it with the specific intention of hiding it from her, she`d go ballistic and I`d be in the **** for weeks.

---

### Post by deBALZAC on 2009-10-21
Thx all for the help :)

---

### Post by DeMus on 2009-10-21
> **deBALZAC said:**
> Thx all for the help :)

So, what will you do now? Get a better relationship with your girlfriend, or try to hide the stuff for her?
Let us know please.

---

### Post by stinkeye on 2009-10-22
He might want to hide a draft of his marriage proposal for all you lot know.:roll:

---

