---
title: "mp3 preview"
date: 2011-11-03
forum: General Help
---

### Post by sblackwell on 2011-11-03
sorry to ask such a simple question but i updated to 11.10.  in previous versions I could hover the mouse over the thumbnail view of a mp3 file and it would play. easy and quick way to preview. now it will not do this I have to open it with a player to preview file

---

### Post by WorMzy on 2011-11-03
Check in nautilus' preferences; you used to be able to enable/disable it in there.

---

### Post by sblackwell on 2011-11-04
not sure exactly what to change in nautilus to achieve this

---

### Post by WorMzy on 2011-11-04
Well, I haven't used nautilus in a significant amount of time, and I wouldn't be surprised if the GNOME developers decided to ax this option as well as any other useful configuration options in their GNOME3 "upgrade", but, before, there used to be an option labelled something like "Enable sound preview" along with the image thumbnail and text document preview options.

---

### Post by pqwoerituytrueiwoq on 2011-11-04
the option is/was there is there in a beta 11.10 i have in a virtual box
i have not tried it to see if it works and don't feel like downloading the codecs to do it with my crap Internet (832 Kbps / 160 Kbps)

---

### Post by hansdown on 2011-11-04
Hi sblackwell.

In 11.10, you need to install

```
SUSHI
```

It's in the repos, and re-adds what nautilus used to do.

I found it in synaptic, but the software center pops up something different.

It works a little differently.

```
mc4man
Fresh Ground Ubuntu
 
Join Date: Jun 2007
Beans: 8,940
	
Re: How to Re-Enable Hover Auto play in 11.10???
The audio preview has been replaced by 'sushi', which previews both audio & video.
Its a bit different, some may like, others not.
to see -
Code:

sudo apt-get install gnome-sushi
```

```
Then highlight a file, press spacebar
Note that any file previewed must have codec support enabled in gstreamer - sushi will not warn if support is not there, just won't do anything.
```

---

### Post by sblackwell on 2011-11-04
sushi worked great. thanks for the info.

---

### Post by hansdown on 2011-11-04
You're welcome, sblackwell.

Sorry, for my bad copy and paste job.

:)

Also, thanks to, mc4man, who supplied the info.

---

### Post by darkwalt on 2011-11-09
Is there any way to make the preview automatically close after it finishes previewing the file?

---

### Post by hansdown on 2011-11-09
Hi, darkwalt.

Not sure if there is another way, but clicking the X in the top left corner closes it.

You seem, to have a good set of lungs.:)

---

### Post by darkwalt on 2011-11-10
> **hansdown said:**
> Hi, darkwalt.

Not sure if there is another way, but clicking the X in the top left corner closes it.

You seem, to have a good set of lungs.:)

Yeah, I was hoping that there was a way to automate the process so that it would finish previewing the file, then close out, instead of lingering.  Also, lungs?

---

### Post by hansdown on 2011-11-10
> **darkwalt said:**
> Yeah, I was hoping that there was a way to automate the process so that it would finish previewing the file, then close out, instead of lingering.  Also, lungs?

That would be a nicer way for it to work.

---

### Post by darkwalt on 2011-11-11
possible scripting?

---

### Post by dcstar on 2011-11-11
> **hansdown said:**
> That would be a nicer way for it to work.

Yes, but we all have to live with these *improvements*, don't we?   :-(

Just another thing to add to the loss of functionality list between Gnome 2 and Gnome 3 - that list must be getting pretty long now.

---

