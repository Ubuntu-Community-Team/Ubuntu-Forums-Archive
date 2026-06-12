---
title: "Why can't I navigate to firefox folder via terminal?"
date: 2010-04-30
forum: General Help
---

### Post by The Flying Penguin on 2010-04-30
Ok, I know there is a sticky showing how to install flash for 64 bit systems using a different method then the one I am trying and I may just do that but I need to figure this out.

I downloaded the 64 bit flash plugin from Adobe's site. I have the libflashplayer.so sitting on my desktop. So I tried dragging it to usr/lib64/firefox-3.6.3/plugins like the instructions said to do but I got a permission error. No biggie, I need to start learning how to use the terminal so I decided to try to copy it over via terminal using the sudo command.

The problem is that I cannot navigate to the firefox-3.6.3 folder through the terminal. I knows its there. I can see it and browse its contents using the gui file manager but when try to navigate there via the terminal I get "no such file or folder". I can navigate all the way up to lib64 using the "cd" command but once I try to "cd" into firefox-3.6.3 I get said error.

What could be causing this?

And I should be able to install flash this way right? Or do I have to use the method provided here [http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

Ok wait. I just looked at the sript used in that post and it appears to me that libflashplayer.so gets moved to /usr/lib/mozilla/plugins/

I get the same error message when I try navigate to that in the terminal as well.

What's the deal?

EDIT: I just installed flash using the method in that post and it works but I still want to know why I can't navigate to certain folders via the terminal. It's going to drive me crazy if I don't find out lol.

---

### Post by zuerston on 2010-04-30
> **The Flying Penguin said:**
> Ok, I know there is a sticky showing how to install flash for 64 bit systems using a different method then the one I am trying and I may just do that but I need to figure this out.

I downloaded the 64 bit flash plugin from Adobe's site. I have the libflashplayer.so sitting on my desktop. So I tried dragging it to usr/lib64/firefox-3.6.3/plugins like the instructions said to do but I got a permission error. No biggie, I need to start learning how to use the terminal so I decided to try to copy it over via terminal using the sudo command.

The problem is that I cannot navigate to the firefox-3.6.3 folder through the terminal. I knows its there. I can see it and browse its contents using the gui file manager but when try to navigate there via the terminal I get "no such file or folder". I can navigate all the way up to lib64 using the "cd" command but once I try to "cd" into firefox-3.6.3 I get said error.

What could be causing this?

And I should be able to install flash this way right? Or do I have to use the method provided here [http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

Ok wait. I just looked at the sript used in that post and it appears to me that libflashplayer.so gets moved to /usr/lib/mozilla/plugins/

I get the same error message when I try navigate to that in the terminal as well.

What's the deal?

Remember everything in linux is case sensitive ,I usually do a dir and copy and paste the names so its right also I always just click "Tools" in Firefox and  then "add ons" to install flash.
And you cant do anything much outside of your home dir as regular user. Firefox should be in your home directory too,click "show hidden files"

---

### Post by nothingspecial on 2010-04-30
What happens if you copy and paste```


sudo mv ~/Desktop/libflashplayer.so /usr/lib/mozilla/plugins/
```

---

### Post by The Flying Penguin on 2010-04-30
> **nothingspecial said:**
> What happens if you copy and paste```


sudo mv ~/Desktop/libflashplayer.so /usr/lib/mozilla/plugins/
```


Ok, I just did that and I didn't get any errors although libflashplayer.so is already there now because I followed the guide in that sticky.

And now just to check again, I just tried to navigate to the firefox-3.6.3 folder under lib64 and it works now! I am typing it exactly as I did before but now all of a sudden I can get there. The only thing I have done since then is hibernate and then resume my session. This is really confusing.

Could this just be a Lucid glitch?

cd /usr/lib64/firefox-3.6.3/plugins previously would give me "No such file or folder" and now I am able to enter the folder no problems. :confused:

---

