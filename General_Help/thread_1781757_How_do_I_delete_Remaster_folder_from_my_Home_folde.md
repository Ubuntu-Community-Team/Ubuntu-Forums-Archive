---
title: "How do I delete Remaster folder from my Home folder?"
date: 2011-06-13
forum: General Help
---

### Post by iam2 on 2011-06-13
[SIZE=4]I have Ubuntu Jaunty 9.04 updated to 9.10 and have downloaded Remaster from Remastersys.  I followed all of the instructions, which were simple enough.  However, there must be some instructions missing as the process failed.  Working with Remaster through Synaptic Manager, the iso was downloaded into my "home" folder into its own Remaster folder.  It was not the iso, like you get when downloading a distro from the Internet, which downloads just an iso onto the Desktop.  Inside the folder were a bunch of empty files (I know, because I opened them) and an iso .  At this point the Remaster instruction stop.  They do not say what to do with the other files, or what they have to do with the iso of my Ubuntu layout.  So, like any other iso (once I knew which one was the iso of my setup), I double clicked on it and it ran me through the process of accessing the DVD to burn it.  Which I did.  I tested it and it failed with some kind of message to the effect that certain files were missing or it could not read it.  So, I thought, I would have to do the 'hunt and peck' method and experiment a few times like I did with the ordinary distro downloads until I get it right.  But first, I would have to dump the Remaster folder in the "home" folder since it took up so much space on my hard drive.  Wrong!  I come to find out it is in something called "root" and that I do not have permission to do anything with it but "copy" it.  Great.  Just great!  Now what do I do.  I tried to change permissions, but was not allowed to do that either.  The only thing I could think of - and dread - was the idea of having to wipe my hard drive and go through the whole reinstall procedures, which takes me days, just because Remaster has locked itself into my system - and there is no 'back door' to get out of it.  Thanks a lot Remaster.  Then I thought of the Forum and thought some wise experienced Linux man would answer this for me and tell me how to get the folder out of the 'home' folder' without having to wipe my hard drive just for that one stupid folder.  Will that wise man please stand up?  I sure would appreciate it.  Boy, I hate Windows because they pull that trick all of the time.  They do not give you the exit and how to back out of a situation.  Now I get it from Linux.  What a disappointment.  So, will someone please help me with this?[/SIZE]

---

### Post by wolfen69 on 2011-06-14
Did you try and delete it as super user?
```
gksu nautilus
```
Then navigate to the file and delete it.

---

### Post by iam2 on 2011-06-14
[SIZE=4]Thank you for your quick response.  No, I have not tried "super user," and I do not know what that is, so I really appreciate the code.  I will try that and read some about "super user" too, and get back to you and let you know how it turned out.  Thank you again.[/SIZE]

---

### Post by ezsit on 2011-06-14
When you run the remastersys program, one of the menu options is to clear or empty the working directory (delete the contents of /home/remastersys/remastersys, yet leaving the empty directories).

---

### Post by kanishkdudeja on 2011-06-14
For any administrative operation, you need to be become the super user.

Run this command and all will be fine for you:

```
sudo remastersys clean
```

it will ask for your password

Enter the password and press Enter.

Done! :)

---

### Post by iam2 on 2011-06-15
[SIZE=4]wolfen69:
It worked!  I was able to delete the folder.  What a relief.  I do like back doors and knowing there is a way out and make right whatever it is that went wrong.  I read up on "super user" and now know what that is too.  Thank you again for making the learning experience easy.
[/SIZE]

---

### Post by iam2 on 2011-06-15
[SIZE=4]ezsit:
Thank you.  I did work my way through Remaster's options from "g" to "a", and did "clear the cashe and history", but do not remember the "clear working directory" option.  The fact that the "documents" in the Remaster folder were blank indicates that one of the options I chose probably caused it.  However, I fail to see the connection to the "documents" in the Remaster folder had anything to do with critical information getting over into the iso Remastering process, which stopped the Remastered distro of my Ubuntu Jaunty OS from booting up on Restart.  Is there a connection?
[/SIZE]

---

### Post by Azdour on 2011-06-15
Hi,

Correct me if I am wrong but if you use:

```
gksu nautilus
```

To delete something it will end up in roots trash unless you use shift+delete. I made this mistake some time ago and wondered why I was running out of disk space until I found that the root trash contained lots of previously deleted files.

---

### Post by inameiname on 2011-06-15
I think you are right.


You could also just try:


gnome-terminal -x sudo chown -R username:username /home/remastersys

...and then delete the folder

---

### Post by iam2 on 2011-06-15
[SIZE=4]kanishkdudeja:

Thank you. wolfen69 helped me with the "super user" process. I did not test the command (sudo remastersys clean) you offered, and have since already deleted the folder. Perhaps I will be able to experiment with it when I next encounter the problem. I am a little unclear, however, by what you mean, "all will be fine for you" once the command is used. For example, exactly what is it that gets "cleaned"? Does it remove everything that is in the "Remaster folder" including the iso? or does it completely remove the now useless Remaster folder with everything in it?[/SIZE]

---

### Post by inameiname on 2011-06-15
I just use the cleanup option in the Remastersys menu. And what it does is delete EVERYTHING inside the /home/remastersys folder, including the ISO. As such, you must first remember to copy the ISO somewhere else, or burn it beforehand.

I actually have a simple script I wrote that'll copy it very easily for you. I'll attach it here.

---

### Post by kanishkdudeja on 2011-06-15
> **inameiname said:**
> I just use the cleanup option in the Remastersys menu. And what it does is delete EVERYTHING inside the /home/remastersys folder, including the ISO. As such, you must first remember to copy the ISO somewhere else, or burn it beforehand.

I actually have a simple script I wrote that'll copy it very easily for you. I'll attach it here.

The command i've told you does the same thing as the cleanup option in the remastersys menu. so yeah it deletes the complete /home/remastersys folder, including the ISO.

---

### Post by inameiname on 2011-06-15
Precisely. I was just letting him know the ISO goes bye-bye too, so back it up beforehand.

---

### Post by kanishkdudeja on 2011-06-16
@inameiname..okay..:)

@iam2: well, i just use the dist option in remastersys. it works for me. if you have any problems with remastersys you can ask at their forums..the link is:
[http://geekconnection.org/remastersys/forums/index.php](http://geekconnection.org/remastersys/forums/index.php)

---

### Post by Azdour on 2011-06-16
Hi iam2,

I got your PM, sorry that I did not explain how to delete trash from the roots trash, please see:

[http://ubuntuforums.org/showthread.php?t=1775524](http://ubuntuforums.org/showthread.php?t=1775524) - post number 7

You may have to press Ctrl+H because directories starting with dot are hidden.

That should tell you how to view the trash and how to permanently delete it. I probably do not have to say this but I will anyway :) When using shift+del as root be careful. Once it is gone its probably gone for good.

---

### Post by inameiname on 2011-06-16
Indeed, [kanishkdudeja]("http://ubuntuforums.org/member.php?u=1152656"). The creator of Remastersys is awesome at helping people on that site. I've had a few issues over the years and he's been huge in getting me through them.

---

### Post by kanishkdudeja on 2011-06-16
yeah..:)

---

