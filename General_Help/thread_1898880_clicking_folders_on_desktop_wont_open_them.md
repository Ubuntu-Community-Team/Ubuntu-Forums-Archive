---
title: "clicking folders on desktop wont open them"
date: 2011-12-22
forum: General Help
---

### Post by pretty_whistle on 2011-12-22
I have lubuntu 11.10.

When I double click any folder on my desktop it doesn't open them.

Later Is set it to single click to open them but I can't open them with this setting either.

If I restart the computer it fixes it temporarily.

It doesn't happen all the time.  
Weird.....

Anyone who can help will be appreciated.  :)

---

### Post by pretty_whistle on 2011-12-22
bump

---

### Post by mystika1 on 2011-12-22
amjjawad may be able to help with this. Bumping for you. I have never had this problem.

Penny

---

### Post by pretty_whistle on 2011-12-22
Thanks!  :)

---

### Post by pretty_whistle on 2011-12-22
I forgot to add this:

It'll do this for a while and then stop on its own.  There's no rhyme or reason to it.

---

### Post by pretty_whistle on 2011-12-22
Even weirder, it only affects folders most of the time.

---

### Post by guyver_dio on 2011-12-23
Are they shortcuts?

I've also had a problem with creating shortcuts/links to folders, usually they'll be fine after i create them but after a reboot they don't work anymore.

The shortcuts are usually to folders on my other hard drives which are formatted as NTFS. I'm thinking this might be the problem as it mounts those drives only when i access them. But I'm still a noob at ubuntu so I'm not sure if this is because it's NTFS or that's just the nature of linux and secondary hard drives regardless of the file system it's using.

---

### Post by pretty_whistle on 2011-12-23
> **guyver_dio said:**
> Are they shortcuts?

I've also had a problem with creating shortcuts/links to folders, usually they'll be fine after i create them but after a reboot they don't work anymore.

The shortcuts are usually to folders on my other hard drives which are formatted as NTFS. I'm thinking this might be the problem as it mounts those drives only when i access them. But I'm still a noob at ubuntu so I'm not sure if this is because it's NTFS or that's just the nature of linux and secondary hard drives regardless of the file system it's using.
No they're not shortcuts.

---

### Post by pretty_whistle on 2011-12-23
I know what the solution is.  Dont use lubuntu.

---

### Post by kalehrl on 2011-12-24
How about just logging out and in again?
I think pcmanfm crashed and that's the reason for your trouble.
This happened to me only once.

---

### Post by amjjawad on 2011-12-24
> **pretty_whistle said:**
> I know what the solution is.  Dont use lubuntu.

Hi there,

IMHO, the solution is: Please do NOT give up, period.

You have started this thread one day ago or perhaps a bit more. I've seen someone with an opened unresolved thread for 6 months and he/she did not give up yet. Please, try to understand ALL of us here are doing this to help and support and this is a volunteer unpaid job but we do enjoy it :)

Having that said, I'm here as a Lubuntu User and one of Lubuntu Family (No, I'm not a developer) to help you and do my best to fix your issue. Are you interested?

---

### Post by amjjawad on 2011-12-24
I'm going to post this and then log out. Hope there will be some progress when I'll be back :)

> PCManFM runs as a daemon and manages your desktop, so when you run it from a terminal it will simply open the PCManFM file manager window instead of starting a new session. You will need to 'killall pcmanfm'
and then run 'pcmanfm --desktop --profile=lubuntu'

To do the above:

1- Menu > Accessories > LXTerminal

2- Run this command: ```
killall pcmanfm
```

If you have icons on your Desktop, these will be gone when you kill PCManFM so don't panic, you'll see them again :)

3- Run this command: ```
pcmanfm --desktop --profile=lubuntu
```

Keep LXTerminal on, don't close it.

4- Now, do whatever you used to do. Click on these folders on your desktop that you were unable to open. If there is something wrong, LXTerminal will show everything. In that case, copy and paste the output it here. Please make sure to wrap up the output with "CODE" tags

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8148[/IMG]


5- To report bugs for PCManFM: [http://sourceforge.net/tracker/?group_id=156956&atid=801864](http://sourceforge.net/tracker/?group_id=156956&atid=801864)

However, I prefer NOT to report anything as of now until we make sure it's really a bug.

If you need more information/help, I'm here :)

Thanks!

---

### Post by pretty_whistle on 2011-12-24
Here it is:

```
(pcmanfm:1538): Gtk-CRITICAL **: IA__gtk_window_present_with_time: assertion `GTK_IS_WINDOW (window)' failed
```

About the above:

I got the same error when it bothered to do it, which was 3 times.  There were a few times I tried to open folders to no avail but it didn't produce output.

---

### Post by pretty_whistle on 2011-12-24
.... and you said not close xterm.  You aren't kidding because when I do the whole desktop disappears now, but I can bring it back with:
pcmanfm --desktop --profile=lubuntu

..... and logging out then in makes the desktop *stay* visible.

As to the problem we're discussing, sometimes the icons to programs on the desktop won't launch either.

---

### Post by pretty_whistle on 2011-12-24
Update:

I never tried this as a solution before: just log out and back in.  So I did it and so far, for the past 10 minutes, everything's fine.

I'll wait and see how long it lasts and whether or not the problem reappears.

---

### Post by pretty_whistle on 2011-12-25
Kalehrl was correct it seems because, as I said in post #15 above, it's looking like simply logging off and back on has saved the day.

Thanks Kalehrl !  :)

[U]
[/U]

---

### Post by pretty_whistle on 2011-12-25
Kalehrl _*did*_ save the day, no maybes about it.  I logged out then in last night and still the issue is gone.  It would've come back by now if the problem was still there!

Yay!

I'll now mark this thread as solved.

---

