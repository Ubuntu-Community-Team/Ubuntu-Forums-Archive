---
title: "Should i update flash or ignore it ?"
date: 2011-04-20
forum: General Help
---

### Post by tmy on 2011-04-20
Hello everyone,
my question is about flash, you see I like to be able to save clips from the web and the way I do it is by looking in my tmp folder and then rename the clip and move to a permanent location. 

Ubuntu updates keeps asking to update flash I don't want to because the last time it moved the convenient location of my video clips from tmp files to another more difficult location on the system, so if I say no will it cause problems to my computers ability or is it a security issue.

Thank you in advance take care everyone


tmy

---

### Post by mike555 on 2011-04-20
You should update the flash, if it is in the update manager, it is for security .

---

### Post by celsdogg on 2011-04-20
> **mike555 said:**
> You should update the flash, if it is in the update manager, it is for security .

+1

Flash has had frequent updates as of late due to huge security issues. For security sake, update flash whenever an update is available.

---

### Post by tmy on 2011-04-20
> **celsdogg said:**
> +1

Flash has had frequent updates as of late due to huge security issues. For security sake, update flash whenever an update is available.

Thank you celsdogg &  mike555,
I suspected this would be the case but it's going to make a mess of my clips being save or store in the tmp files, do you have a method for still being able to have easy access to my clips ? It may sound trivial but I really need to be able to do this as it helps in being able to watch the clip off line and study.

Thank you for you advice and prompt reply please take care


tmy

---

### Post by mike555 on 2011-04-20
if you update and can't find the temp file, maybe an Firefox add-on to get flash videos might be easier...

---

### Post by nitstorm on 2011-04-20
[http://thevoidghost.wordpress.com/2011/03/22/flash-cache-on-ubuntu-linux/](http://thevoidghost.wordpress.com/2011/03/22/flash-cache-on-ubuntu-linux/)

Maybe that could help?

---

### Post by Vaphell on 2011-04-20
> Ubuntu updates keeps asking to update flash I don't want to because the last time it moved the convenient location of my video clips from tmp files to another more difficult location on the system

it's not a difficult location, it's in your browser profile, for firefox the procedure is as follows: ctrl+h to unhide, .mozilla -> firefox -> some_garbage -> Cache
just bookmark it in file browser (ctrl+d) and be done with it - you'll have a shortcut in the left pane

---

### Post by tmy on 2011-04-21
> **Vaphell said:**
> it's not a difficult location, it's in your browser profile, for firefox the procedure is as follows: ctrl+h to unhide, .mozilla -> firefox -> some_garbage -> Cache
just bookmark it in file browser (ctrl+d) and be done with it - you'll have a shortcut in the left pane
Hi Vaphell,
thank you for your reply your way is without doubt a work a round however it is difficult because it involves to many steps before the update I would simply open the tmp folder before playing a clip and I could see the clip appear, rename and find it so easy why has it changed and been made so much more involved and fiddly ?

Thank you again I really appreciate your reply however I wish there was a simpler method. Take care

Many thanks 

tmy 

bye

---

### Post by dino99 on 2011-04-21
FF addon flashvideoreplacer

---

### Post by jmszr on 2011-04-21
tmy,

There is the Firefox add-on Video DownloadHelper: [https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/](https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/) .

 I use it and it works well - it will even convert formats on the fly.

---

### Post by TeoBigusGeekus on 2011-04-21
Read my posts in [this]("http://ubuntuforums.org/showthread.php?t=1688948") thread.

---

### Post by tmy on 2011-04-22
> **jmszr said:**
> tmy,

There is the Firefox add-on Video DownloadHelper: [https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/](https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/) .

 I use it and it works well - it will even convert formats on the fly.

Hello everyone,
thank you for all your help everyone I have tried the various methods and they work well and thank you. I wish the updated flash would still allow the tmp folder as before because it means your independent of add on software and browser add ons also what is the reason the location has been moved ?

Thank you again to everyone who has suggested a work around I still have not updated my flash I like the tmp file option too much. 


Take care everyone and if anyone feels the same as I do regarding flash and the tmp file please reply and if you know a way to still have the update and yet still have the tmp folder location of the clip please reply and share.

tmy 


bye.

---

### Post by Vaphell on 2011-04-22
the reason is that stuff your browser caches should be under browser's control, in 1 place, not scattered around wherever flash or any other plugin feels like it. Flash now obeys rules set by the browser and it's a good thing. Granted, /tmp was convenient but nobody prevents you from creating a direct link to the cache so it's only 1 click away.

---

### Post by tmy on 2011-04-23
> **Vaphell said:**
> the reason is that stuff your browser caches should be under browser's control, in 1 place, not scattered around wherever flash or any other plugin feels like it. Flash now obeys rules set by the browser and it's a good thing. Granted, /tmp was convenient but nobody prevents you from creating a direct link to the cache so it's only 1 click away.

Hi Vaphell,
thank you for getting back to me and explaining that, the problem I have is how can I quickly with one click create a direct link to the cache ? Bear in mind I'm not to good with this but so want to learn.

Please check out this link [http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html](http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html)
It looks great and would be nice to try it out only problem is the link just shows code and then I would have to make the script executable, could you check it out and let me know your opinion of it ?

Thank you again and thanks also to [chetancrasta]("http://ubuntuforums.org/member.php?u=763415") for the original tip and link to this script. Take care

tmy 


bye

---

### Post by Vaphell on 2011-04-23
1. open your home dir with filebrowser
2. if you don't see any objects starting with . press ctrl+h
3. go to .mozilla, firefox, some_random_gibberish.default (randomly generated name of your profile), Cache
4. press ctrl+d to bookmark the location, it will be shown in the left pane of filebrowser

the problem i see at least on my box while writing this very post is that i have a huge maze of directories which i don't recall having earlier, when i searched for youtube clips when the /tmp -> ~/.mozilla/firefox/something/Cache switch occured.
I used to have all stuff in 1 place (which made it possible to find flash file simply by sorting by date), now it's all scattered around 1-2 files/dir.
That may prove troublesome to find the file you want.

if you want to try that perl script out - you just need to make the script file executable
ctrl+s to save page or manually copy the text, paste it into a file,
right click it, in permissions tab tick the checkbox that allows to execute the file
script seems to work nicely

---

### Post by tmy on 2011-04-23
> **Vaphell said:**
> 1. open your home dir with filebrowser
2. if you don't see any objects starting with . press ctrl+h
3. go to .mozilla, firefox, some_random_gibberish.default (randomly generated name of your profile), Cache
4. press ctrl+d to bookmark the location, it will be shown in the left pane of filebrowser

the problem i see at least on my box while writing this very post is that i have a huge maze of directories which i don't recall having earlier, when i searched for youtube clips when the /tmp -> ~/.mozilla/firefox/something/Cache switch occured.
I used to have all stuff in 1 place (which made it possible to find flash file simply by sorting by date), now it's all scattered around 1-2 files/dir.
That may prove troublesome to find the file you want.

if you want to try that perl script out - you just need to make the script file executable
ctrl+s to save page or manually copy the text, paste it into a file,
right click it, in permissions tab tick the checkbox that allows to execute the file
script seems to work nicely
Hi Vaphell,
your going to kill me but I'm struggling, I made the script executable and ran it but it just flashed the console box up for a moment and then it went off. I want to be able to save a clip from the BBC news web site for example a clip of an interview with a manager after a game. How can I do this using the script ?

Where will it be saved ? Could you please talk me through it because I'm almost there just can't seem to figure how to do this sorry to be a pain hope you still have the patience to help. Thank you again for all your help. Just a note I have not yet installed the latest flash maybe that is why the script is not working ? I copied the script to a gedit text file and saved it then did the right click permission ticked the executable box.

Hope some one else is following this and it helps them also.  

tmy

---

### Post by tmy on 2011-04-29
> **tmy said:**
> Hi Vaphell,
your going to kill me but I'm struggling, I made the script executable and ran it but it just flashed the console box up for a moment and then it went off. I want to be able to save a clip from the BBC news web site for example a clip of an interview with a manager after a game. How can I do this using the script ?

Where will it be saved ? Could you please talk me through it because I'm almost there just can't seem to figure how to do this sorry to be a pain hope you still have the patience to help. Thank you again for all your help. Just a note I have not yet installed the latest flash maybe that is why the script is not working ? I copied the script to a gedit text file and saved it then did the right click permission ticked the executable box.

Hope some one else is following this and it helps them also.  

tmy
Hello Vaphell,
I was wondering if you care to explain how the script is supposed to work I made it executable and ran it but the console box popped up fro a second and as far as I can see nothing else happened. What is it supposed to do ? I don't want to install the flash update unless I can find a convenient method of locating saving and renaming the flash files that were so easy to work with when they appeared in the tmp folder.

I would really appreciate your help explaining the script and what it is supposed to do before I update the flash. Thank you in advanced take care.


tmy 


bye.

---

### Post by tmy on 2011-05-05
> **tmy said:**
> Hello Vaphell,
I was wondering if you care to explain how the script is supposed to work I made it executable and ran it but the console box popped up fro a second and as far as I can see nothing else happened. What is it supposed to do ? I don't want to install the flash update unless I can find a convenient method of locating saving and renaming the flash files that were so easy to work with when they appeared in the tmp folder.

I would really appreciate your help explaining the script and what it is supposed to do before I update the flash. Thank you in advanced take care.


tmy 


bye.
Hello,
could I ask has this subject gone cold ? I asked if someone could explain what the script was supposed to do ? And when I made it executable and ran it but the console flashed up for a blink of an eye then off and nothing appeared to happen. I don't want to update the flash for the reasons mentioned earlier. I understand the security problems from not updating. So to just be clear if I run the script without first updating the flash the result would be no effect as it is only going to work after the flash is updated ?

And what is the script going to do after first updating flash ( where will the flash be moved to ) Thank you and please be gentle as I don't understand that is why I have come here for guidance I can't understand why no one has replied, if we are to encourage Linux Please encourage people don't ignore them. Thank you take care.

tmy

---

