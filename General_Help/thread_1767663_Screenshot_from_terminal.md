---
title: "Screenshot from terminal?"
date: 2011-05-26
forum: General Help
---

### Post by conradin on 2011-05-26
Hi all, 
is there anyway I can perform a screen capture, or screen shot?
This is for a Ubuntu server, with no GUI. 
Can I get a code example?

---

### Post by dandnsmith on 2011-05-26
What are you trying to capture. A screen capture without a GUI doesn't seem to make sense to me. Perhaps you're trying to log what happens in a terminal window - if so, then I use vi, and execute the commands from there (eg :r! date to get date/time) so I can record a sequence.

HTH

---

### Post by nothingspecial on 2011-05-26
Well, it depends what you want to do. You could use script to capture a terminal session. See man script (or post back).

Or if you want an actual screenshot use fbgrab something like this

```
fbgrab -c 1 -s 5 screenshot.png
```

You can run that from tty2 and it will grab tty1 after a five second delay.

Then view it with fbi

```
fbi screenshot.png
```

---

### Post by conradin on 2011-05-26
I tried ```
sudo fbgrab -c 5 term5.png
```
what I got is the attached image.
its all chopped, an look like its not synching. 
The man page to fbgrab says not to use the -s option in conjunction with -c so I didnt.

---

### Post by nothingspecial on 2011-05-27
If you don't mind, what is on the screen that you are trying to capture?

fbgrab works perfectly for me, even when playing videos.

It could be something to do with permissions on the framebuffer. Do you get any errors when running fbgrab?

---

### Post by conradin on 2011-05-27
I do have to use sudo to get fbgrab to work. 
The only error is the output is screwy. I can see the red white and blue in the horizontal shifting lines there so its getting something related to the screen capture. No other errors that I see. 

I also installed fbi, that works fine, just like any otehr image viewer.

---

### Post by MartyBuntu on 2011-05-27
I doubt a screen cap will work without X running.

---

