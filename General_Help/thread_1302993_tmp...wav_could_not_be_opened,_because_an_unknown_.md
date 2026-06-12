---
title: "/tmp/...wav could not be opened, because an unknown error occurred."
date: 2009-10-27
forum: General Help
---

### Post by YMS_1975 on 2009-10-27
[B]/tmp/200910262059-6472106342-3.wav could not be opened, because an unknown error occurred.

Try saving to disk first and then opening the file.[/B]

Does anybody know what this error message is about?! I can't open up my voice mails (in .wav format) from my e-mails anymore.

I click on the .wav file, select "Open with...Movie Player (default)" dialog box, then click "ok" and that's when I get the error message.

WTF?! :)

Ok, I'll take it down a notch. But seriously, it's annoying. I used to be able to listen to my voice mails, but now? NOTHING.

---

### Post by dcstar on 2009-10-27
> **YMS_1975 said:**
> [B]/tmp/200910262059-6472106342-3.wav could not be opened, because an unknown error occurred.

Try saving to disk first and then opening the file.[/B]

Does anybody know what this error message is about?! I can't open up my voice mails (in .wav format) from my e-mails anymore.

I click on the .wav file, select "Open with...Movie Player (default)" dialog box, then click "ok" and that's when I get the error message.

WTF?! :)

Ok, I'll take it down a notch. But seriously, it's annoying. I used to be able to listen to my voice mails, but now? NOTHING.

Have you run out of space in /tmp or your root (/) filesystem?

---

### Post by YMS_1975 on 2009-10-27
> **dcstar said:**
> Have you run out of space in /tmp or your root (/) filesystem?

Not sure...but I don't see how as I've got 264 GIGS of free hard disk space.
I'm lost on this one.

I think it's a CODEC issue.

---

### Post by Jayferd on 2009-10-27
What's happening is that when you click "Open With...", your browser is trying to save the file in the /tmp directory, and i'ts hitting some error either in writing to or reading from that directory.  Could you open up Disk Usage Analyzer and do a full system scan?  Let us know (a) the size of your /tmp directory, and (b) the amount of free space in it.

If you'd like to start listening to your voice-mails before you fix this, you can just click "Save File" instead of "Open With...", and it'll save the file either on your desktop or in ~/Downloads or in whatever folder you've manually specified.  You can open them from there, or run it from your browser (are you running firefox?)

---

### Post by Jayferd on 2009-10-27
whoops, I leapfrogged your last post.  If you've got that much free space, try the save as... thing.  Also, what happens when you try to open .wav files from other sources?

---

### Post by YMS_1975 on 2009-10-27
> **Jayferd said:**
> whoops, I leapfrogged your last post.  If you've got that much free space, try the save as... thing.  Also, what happens when you try to open .wav files from other sources?

I've tried saving it to my desktop, and when I open it....nothing happens. It just won't play. I've also got VLC installed, and nothing.

:confused:

---

### Post by Jayferd on 2009-10-28
Hm.  Can you get a wav file from somewhere else?  I'm just wondering if somehow the specific files you've got all have some quirk that totem doesn't want to read.

---

### Post by YMS_1975 on 2009-10-28
> **Jayferd said:**
> Hm.  Can you get a wav file from somewhere else?  I'm just wondering if somehow the specific files you've got all have some quirk that totem doesn't want to read.

I don't think it's a problem with the .wav file itself, because I was able to listen to them before. Nothing has changed with the files, as far as I can see.

---

### Post by Jayferd on 2009-10-28
...okay... I'd recommend trying another wav file anyways, it might be helpful.

Otherwise, you could check which gstreamer plugins you have installed.  Do a search in Synaptic for gstreamer, you should have the good, bad, and ugly plugins installed.

As an alternative temporary solution, you can convert to flac with the command-line tool flac
```

sudo aptitude install flac

```

and then run
```

flac my_voicemail_message.wav

```

to create a flac version of your wave file.  This you should be able to open in Totem without a problem.

---

### Post by YMS_1975 on 2009-10-29
Well,

I uninstalled Totem, and gstreamer. So all I have now is VLC. Here's the funny thing : 

1) If I download any other .WAV file off the net to my desktop, VLC it **will** in fact play it. It just seems to be my voice mail .WAV's.  :(

2) If I click on any other .WAV file, I'm forced to download it to my desktop. I don't see an option to **Open from... **(and I'd pick VLC if this dialog box was listed)

Why am I forced to save it to my desktop and I can't open the file using VLC?

---

### Post by Jayferd on 2009-10-29
Hm.  It doesn't seem like your desktop is the problem.  I'm no audio guru, but I believe there are different types of .wav's, some of which are proprietary (read: M$).  So I'm suspecting that you are missing some gstreamer plugins.  What do you see when you do a search in Synaptic for "gstreamer"?  The plugins have names like "gstreamer0.##-good", "gstreamer0.##-bad", and "gstreamer0.##-ugly".

If all else fails, I do recommend that flac thing, if it works.

---

### Post by YMS_1975 on 2009-10-29
> **Jayferd said:**
> Hm.  It doesn't seem like your desktop is the problem.  I'm no audio guru, but I believe there are different types of .wav's, some of which are proprietary (read: M$).  So I'm suspecting that you are missing some gstreamer plugins.  What do you see when you do a search in Synaptic for "gstreamer"?  The plugins have names like "gstreamer0.##-good", "gstreamer0.##-bad", and "gstreamer0.##-ugly".

If all else fails, I do recommend that flac thing, if it works.

I could do the "flac thing" but it raises the question : Why did it work before, and not now? 

I'm praying that this problem will be resolved after my update to 9.10 Karmic Koala (which I'm doing RIGHT NOW)  :D

---

### Post by Giblet5 on 2009-10-29
> **YMS_1975 said:**
> I don't think it's a problem with the .wav file itself, because I was able to listen to them before. Nothing has changed with the files, as far as I can see.

Nothing HAS to change on your system.

Those .wav files didn't come from your system, did they? They came through email, right?

Nothing can mangle an attached file faster than a botched server configuration change.

The best thing to do is to open a known good .wav file -- one you saved last week should be good. If it plays, and new ones don't.........

---

### Post by Jayferd on 2009-10-29
That would totally make sense if it came through email.  I was assuming YMS was downloading from a voicemail service like AT&T and Comcast (shiver) provide.  Although I wouldn't put it past them to botch their server configs either...

---

### Post by frank cox on 2010-11-05
> **Jayferd said:**
> That would totally make sense if it came through email.  I was assuming YMS was downloading from a voicemail service like AT&T and Comcast (shiver) provide.  Although I wouldn't put it past them to botch their server configs either...

I had the same problem but the ugly plugins did not help.  However the file played perfectly in VLC.
VLC rocks!

---

