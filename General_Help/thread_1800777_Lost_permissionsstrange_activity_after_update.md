---
title: "Lost permissions/strange activity after update"
date: 2011-07-09
forum: General Help
---

### Post by CleveRuse on 2011-07-09
Ok I'm LOST!  First off, Im on Natty using Gnome Classic as Desktop. I've been having strange things happening since some programs updated ( like losing my Network Connection icon and having it show up now on the secondary users desktop, while it used to be that she couldn't get it to display, now I can't.)

So I try to theme an app using APK Manager but now my 'out' folder is X'ed out, along w/ its contents, and it says I don't have permissions to view the folder/files. So i checked and I'm still the owner, my perms are all checked, I believe my group is still the same (same as my user name). Under 'System/Administration/User and Groups' I see that I'm still an Admin., I have all  User Privileges marked true, my main group matches my user name and my ID is still 1000. Also my password is still valid. Please, someone tell me WTF is happening here, LOL. Thnx in advance for ur patience and concern:(

---

### Post by matt_symes on 2011-07-09
Hi

I know you have checked this but it does not hurt to double check.

Navigate to the folder containing your 'out' folder and type

```
ls -ld out
```

That is small L before the d above. Also type 

```
groups
```

Post the results back here using copy and paste.

Kind regards

---

### Post by CleveRuse on 2011-07-09
ok, here. for the first one:

ab@CleveRuse-LT20:~/sdk/tools/apk_manager$ ls -ld out[COLOR=SeaGreen]
[/COLOR] [COLOR=Blue]drwxr-xr-x 5 root root 4096 2011-07-09 12:35 out
[/COLOR] 
And for groups:

ab@CleveRuse-LT20:~/sdk/tools/apk_manager$ groups
[COLOR=RoyalBlue][COLOR=Blue]ab adm dialout fax cdrom floppy tape audio dip video plugdev fuse netdev lpadmin admin sambashare cle[/COLOR]ver[/COLOR]
ab@CleveRuse-LT20:~/sdk/tools/apk_manager$

---

### Post by matt_symes on 2011-07-09
Hi

> **CleveRuse said:**
> ok, here. for the first one:

ab@CleveRuse-LT20:~/sdk/tools/apk_manager$ ls -ld out
[COLOR=Red][SIZE=1]drwxr-xr[/SIZE]-x 5 root root 4096 2011-07-09 12:35 out[/COLOR]

That folder is owned by root but you still should have read access to it.

> 
And for groups:

ab@CleveRuse-LT20:~/sdk/tools/apk_manager$ groups
[COLOR=Red]ab adm dialout fax cdrom floppy tape audio dip video plugdev fuse netdev lpadmin admin sambashare clever[/COLOR]
ab@CleveRuse-LT20:~/sdk/tools/apk_manager$

You are user ab and your main group is ab.

What happens if you type

```
ls -l ~/sdk/tools/apk_manager/out
```

Post back the results.

You could change the owner of the directory to your user and group but i am not sure  of the implications of doing that in this case.

Kind regards

---

### Post by CleveRuse on 2011-07-09
k, hold on... thnk u btw:)

---

### Post by CleveRuse on 2011-07-09
here:
[quote]
ab@CleveRuse-LT20:~$ ls -l ~/sdk/tools/apk_manager/out
[COLOR=Red]total 88[/COLOR]
[COLOR=Red]-rw-r--r-- 1 root root  4584 2011-05-15 00:46 AndroidManifest.xml
-rw-r--r-- 1 root root 61152 2011-05-15 00:46 classes.dex
drwx------ 3 root root  4096 2011-07-09 12:35 [COLOR=RoyalBlue]lib[/COLOR]
drwx------ 2 root root  4096 2011-07-09 12:35 [COLOR=RoyalBlue]META-INF[/COLOR]
drwx------ 8 root root  4096 2011-07-09 12:35[COLOR=RoyalBlue] res[/COLOR]
-rw-r--r-- 1 root root  6884 2011-05-15 00:45 resources.arsc[/COLOR]
ab@CleveRuse-LT20:~$ 
[quote]

the blue texts are highlighted in blue in my terminal too so i did the same(?)

---

### Post by matt_symes on 2011-07-09
Hi

> ab@CleveRuse-LT20:~$ ls -l ~/sdk/tools/apk_manager/out
[COLOR=Red]total 88[/COLOR]
[COLOR=Red]-rw-r--r-- 1 root root  4584 2011-05-15 00:46 AndroidManifest.xml
-rw-r--r-- 1 root root 61152 2011-05-15 00:46 classes.dex
drwx------ 3 root root  4096 2011-07-09 12:35 [COLOR=RoyalBlue]lib[/COLOR]
drwx------ 2 root root  4096 2011-07-09 12:35 [COLOR=RoyalBlue]META-INF[/COLOR]
drwx------ 8 root root  4096 2011-07-09 12:35[COLOR=RoyalBlue] res[/COLOR]
-rw-r--r-- 1 root root  6884 2011-05-15 00:45 resources.arsc[/COLOR]
ab@CleveRuse-LT20:~$ 

Well you can  see in the directory 'out' using the terminal so that is good. 

Is it only using Nautilus filesystem browser that you cannot see in the 'out' directory ?

> 
[COLOR=Red]drwx------ 3 root root  4096 2011-07-09 12:35 [COLOR=RoyalBlue]lib[/COLOR]
drwx------ 2 root root  4096 2011-07-09 12:35 [COLOR=RoyalBlue]META-INF[/COLOR]
drwx------ 8 root root  4096 2011-07-09 12:35[COLOR=RoyalBlue] res[/COLOR][/COLOR]

You will not be able to see inside these directories as they are owned by root and you do not have read access to them.
[COLOR=Red][COLOR=RoyalBlue][/COLOR][/COLOR]
Kind regards

---

### Post by CleveRuse on 2011-07-09
Lol, IDK, i just looked in my SDK and saw it X'ed out. how do i not use Nautilus?

---

### Post by matt_symes on 2011-07-09
Hi

If you can see inside the 'out' directory using Nautilus but not in the other directories inside 'out' then Nautilus is working fine as you do not have permissions to view inside those directories as your user. :P

Kind regards

---

### Post by CleveRuse on 2011-07-09
yeah, I can open 'out', but cant open anything inside.

---

### Post by CleveRuse on 2011-07-09
I'm sure I could open as ROOT, but obviously that's not the point.

---

### Post by CleveRuse on 2011-07-09
Just yesterday this worked fine

---

### Post by matt_symes on 2011-07-09
Hi

You could change the permissions but i am not sure of the implications of that as i do not use the application.

Kind regards

---

### Post by CleveRuse on 2011-07-10
Ok, well I'm not sure i understand. How do I change perms for a folder that belongs to root? I could chmod but that's not permanent, right? Ur othersolution to change owner n group is probably better, expecially since I don't believe they belonged to Root before yesterday. I'll do a Google search for the commands. Thnx!

---

### Post by CleveRuse on 2011-07-10
ok apparently chmod is permanent, lol, Ive been 'chmod'ing every time for things.

anyway, I gained access by changing the owner, group and permissions. first i typed in terminal: 

[COLOR=Navy]chown -R 'my-user-name':'my-group-name /path-to-'out'-folder[/COLOR]

while logged in as root. Then typed:

[COLOR=Navy] chmod -R 755 /path-to-'out'-folder[/COLOR]

And it worked:) yea!

.................So then i proceeded to modify an apk file and install in phone but i didnt like how it looked so i went back to APK Mgr, ran the script, extracted the files then went to view them in the 'out' folder and guess what............. IT'S F*$#ING LOCKED AGAIN! come on man... WTF? Ubuntu, wut r u doin to me?

---

### Post by CleveRuse on 2011-07-10
so I checked and of coarse it belongs to ROOT again. Do I need to save the changes somehow? I don't remember reading that anywhere.

---

### Post by matt_symes on 2011-07-10
Hi

Here is a walkthrough by someone who installed it in Linux Mint.

[http://www.youtube.com/watch?v=QlaFHNC1DIs](http://www.youtube.com/watch?v=QlaFHNC1DIs)

It's not a program i use so i may not be the best person to answer. I notice he does change the owner and permissions of the files though.

Kind regards

---

### Post by CleveRuse on 2011-07-10
thnx, i think ill go visit XDA. They have a thread over there bout APK Manager but i came here cuz i think its a Ubuntu problem. I just cant understand this. I mean its not like I just tried to install this. Ive had it installed and working correctly for a couple months on Ubuntu (not to mention Windows before that) I need to figure out why 'Root' keeps steeling these folders now? I created them. How does Root all of the sudden own them? As for the youtube tutorials with no sound, they just drive me absolutely insane. hell Im prolly loosen out cuz of it but i just cant watch them, lol.

---

### Post by CleveRuse on 2011-07-10
ima change the name of this thread tho.

---

