---
title: "Every file wants to be opened as a text file"
date: 2010-02-28
forum: General Help
---

### Post by vizitorq on 2010-02-28
Images, PDFs, docs, Videos, everything wants to be opened in either gedit or openoffice. I have no idea why. What can I do?!?! I didn't do anything and for some reason everything thinks it's a text file. Some files still have the right icons, some image icons are screenshots, some video file icons are screenshots, but most are text-file icons.

When I right-click a PDF and say to open in "Document Viewer", it gives me this error

File type application/octet-stream type (application/octet-stream) is not supported

what?! WHY!? What is going on!?

---

### Post by vizitorq on 2010-02-28
bump

---

### Post by asmoore82 on 2010-02-28
:shock:I'm puzzled :confused:
~
you could boot off of a Live CD to see if something has corrupted the files themselves.

---

### Post by vizitorq on 2010-02-28
honestly I'm thinking it has something to do with gedit. I added some plugins to make it more like textmate and ever since then everything wants to be opened up in gedit. I tried removing gedit, and deleting all files associated with gedit, but that didn't help at all.

what could have possibly corrupted every single file??

---

### Post by sgosnell on 2010-02-28
It's not corrupted, and removing gedit won't help.  You need to return the file associations to the proper packages.  It's the same with Windows - file extensions are associated with apps.  Open Nautilus, click Edit/Preferences, and set the file types to be opened with the package you prefer, or you can set them to "Ask" each time.  The plugins you installed, whatever they were, apparently reset all that, and you'll have to reset them again manually.

---

### Post by dcstar on 2010-02-28
> **vizitorq said:**
> honestly I'm thinking it has something to do with gedit. **I added some plugins **to make it more like textmate and ever since then everything wants to be opened up in gedit. I tried removing gedit, and deleting all files associated with gedit, but that didn't help at all.

what could have possibly corrupted every single file??

"what?! WHY!? What is going on!?"......

The answer look pretty obvious......

---

### Post by vizitorq on 2010-02-28
> **dcstar said:**
> "what?! WHY!? What is going on!?"......

The answer look pretty obvious......

ya maybe for someone who's has 8,000 posts in the forums. As far as forums go, I have 1% of your experience.

---

### Post by vizitorq on 2010-02-28
> **sgosnell said:**
> It's not corrupted, and removing gedit won't help.  You need to return the file associations to the proper packages.  It's the same with Windows - file extensions are associated with apps.  Open Nautilus, click Edit/Preferences, and set the file types to be opened with the package you prefer, or you can set them to "Ask" each time.  The plugins you installed, whatever they were, apparently reset all that, and you'll have to reset them again manually.

Thanks for your suggestion, but I'm afraid the problem is much worse than that. When performing your instructions I noticed that Nautilus only asks for specifics on how to handle media files. It's not just media files that's the problem, it's every file. And even files that are supposed to be opened in word, still won't open.

---

### Post by vizitorq on 2010-03-01
looking into it further, it seems that for some reason my computer thinks that every file's mime-type is "text/plain".

I found out by displaying all files in "list-view" in the nautilus file-browser. What could possibly have caused this. And more importantly, how can I restore all mime-types to their original state?

something with /usr/share/mime/ right?

---

### Post by dcstar on 2010-03-01
> **vizitorq said:**
> ya maybe for someone who's has 8,000 posts in the forums. As far as forums go, I have 1% of your experience.

The point is you changed something and there was a direct negative side-effect, and you didn't even bother to tell people of the change in your original post - you said "I didn't do anything"!!!

Just tell people what you actually did and that gives them a chance of trying to come up with a solution - otherwise you are just delaying any possible fix.

---

### Post by todak on 2010-03-01
> **vizitorq said:**
> ...and more importantly, how can I restore all mime-types to their original state?

something with /usr/share/mime/ right?

Right-click on a file of your choosing. Click **Properties**, then **Open With**. You will then be shown a list of applications that can be used to open the file. For instance, if you select a .jpg file, you will be able to choose from Gimp, Image Viewer, F-spot or whatever application you have installed for image viewing/editing. Click on the app that you want to be associated with .jpg files and it will set that app, for all .jpg files, as the default. Do the same for each file type. You may also remove the offending app from the list of apps that you can use to open a file. For a .jpg, for instance, I do not think a text editor is wanted or needed to view or edit an image file. Simply select the gedit app from the **Open With** list and click the **Remove** button

---

### Post by sgosnell on 2010-03-01
DCstar has it right, the reason for the changes is obvious.  You added text plugins to Nautilus.  Those changed the associations to text.  Adding plugins is [b]not[/] doing nothing.  And yes, Todak is right, you have to do it manually for filetypes not listed in the dialog I pointed you to.  

You have to be willing to accept responsibility for what you do, not try to blame everything on some unknown force.  Tell us exactly what you did, and we have a much better chance of helping you.

---

