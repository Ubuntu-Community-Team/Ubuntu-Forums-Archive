---
title: "Shared Documents"
date: 2006-06-13
forum: General Help
---

### Post by mafitzpatrick on 2006-06-13
How would I set up an equivalent of a Shared Documents folder on an Ubuntu installation. I have 2 users on the computer & want a location where both can access files. Is there a "correct" location / something already set up?

If not is this is the way I was thinking of going about it...

[LIST]
[*]create a directory
[*]sudo chown :users directory
[*]put files in there
[/LIST]

Any suggestions?

---

### Post by Joeb on 2006-06-13
I would create a directory under /home for the shared folder and also create a group that has read/write access to it.  If you don't want to make the group, you could change the permissions on the directory to 777 and then anybody on the computer has full access to it.

---

### Post by mafitzpatrick on 2006-06-14
Thanks for that Joeb, it's good to know I wasn't too far off mark.  Would setting it to group "users" not work though? I imagined (perhaps wrongly) that this would give ownership and access to all users.  I guess I would need to change the permissions to give the group users relevant permissions anyway in case it was set to group->view?

How about files that are place inside it? Do I need to do anything specific to enable everyone to read/write to files there regardless of who saved last?

I'm thinking if this can be worked out it might be worth having this added into future releases. Migrating from Win XP I kind of "expected" it to be there & it is useful when you have more than one user set up.  Easier to add to the install than for new people to work it out (although it's a useful learning experience I guess!)

Thanks again for the help, appreciated.

---

### Post by Joeb on 2006-06-14
You can use the group users to accomplish what you want, however, if there is ever going to be somebody you don't want to have access, then that group would not be the best choice.  However, for the purpose you describe, it should be fine.

If you set up the folder first and assign the ownership before moving the files, then you shouldn't have to do anything else.

As for not having it set up by default, I think that is by design.  Unlike Windows, Linux and the other Unix variants strive for security first.  As such, users have zero access unless it is granted to them.  Contrast that with Windows, where users have pretty much full access unless it is taken away.

The Linux/Unix security model, creates a little more work to set things up, but it's also what makes it very difficult for virus attacks and the like.  It also makes it difficult for an inexperienced user in the house from messing up anything on the shared computer other than their own home directory (unless you have given them the ability to do so).

Hope that helps.

---

### Post by mafitzpatrick on 2006-06-17
Thanks for the help there - I've got that set up and working just fine. Thinking about it I can see the sense on not having something like this set up by default - although a nice UI to manage would be good.  I realise having a "known" open-access area on a computer isn't very sensible - perfect target for malicious software.

Thanks again!

---

### Post by mafitzpatrick on 2006-06-19
Showing incredibly bad form replying to my own thread again, but....

I have this shared folder set up and working, using the owner/group martin:users (martin being my login, and users containing all users) and this works fine.  If it aint broke don't fix it you might say, but if I change the owner to "root" or "nobody" (still with group users) no users can now access the folder/files.

I've tried checking out file permissions help stuff but it's all a bit thick.  Basically - what's going on here? If you set a user as the owner, does that user also have to be in the group you're using? (i.e. would "nobody" or "root" need to be in "users" for it to work)? What is the rule for who can access it if not? Root only?

Also, I kind of assumed that the group "users" would automagically contain all users on the system, but it doesn't - I had to add them manually. Is this normal? Not important, just interesting!

---

### Post by Uber-n00b on 2008-05-04
I've only migrated from XP to (dual-booting) Ubuntu a week ago and that's all the linux experience I have so far. I really need a directory similar to the *Shared Documents* folder in windows, but I don't understand the above replies. Can somebody give me a step-by-step (or a link) how to create a */home/**shared*** folder and how to make that accessible (read, write, delete, new...) to every user?

I don't even know how to login as root yet but I'm going to figure that out as soon as this is posted. I have gotten comfortable with terminal and synaptic (the only good that came out of fruitlessly trying to get my ATI card on another system working) but other than that, it'd be safe to assume I completely unfamiliar with the OS.

Thanks in advance!

---

### Post by penguin steve on 2008-05-04
open the terminal and type the following (one command at a time)
```

sudo mkdir /home/shared
sudo chmod 777 /home/shared

```
thats it! hope it helps

---

### Post by Uber-n00b on 2008-05-04
hmmm... i tried the provided code posted immediately above in Terminal with partial success. ( /home/shared was created but I can't open files saved there by one user when logged in as another.) I used the Terminal code using the account created when I installed ubuntu. Here's what happens when I try to open a file in the shared dir with the other login acct.

[IMG]http://i196.photobucket.com/albums/aa263/chisoxfan84/Screenshot-evince.png[/IMG]

and here's the directory itself when logged in as the secondary user. What do those little circles mean?
[IMG]http://i196.photobucket.com/albums/aa263/chisoxfan84/Screenshot-shared-FileBrowser.png[/IMG]

Help me allow everyone to read write to it...Even windows (with the ext2 [[COLOR="Sienna"]fs-driver[/COLOR]]("http://www.fs-driver.org/") if possible. Thanks again.

---

### Post by Uber-n00b on 2008-05-05
Got it working! I looked up how to enable the root login prompt, logged in as root, rt-clicked on the /shared folder and set permissions appropriately. 

Something like that should really come standard I think.

---

### Post by penguin steve on 2008-05-06
glad i helped. i think the problem was that the second command had an extra space or something. i will update once i have tested it.

---

### Post by penguin steve on 2008-05-07
so i have found how to change permissions through the terminal but i dont know how to apply these permissions to the files added AFTER running the code. like an auto chmod as it is moved into the shared folder.

```

sudo chmod -R 777 /home/shared/*

```

so that will do read, write, execute for every file within the shared but if you add a file into the folder after running the code, the file will conserve it's permissions and be read only except for the user who created it. maybe someone else can shed some light on this matter. do you have the same issue uber-n00b now that you seem to have fixed this with the GUI?

---

