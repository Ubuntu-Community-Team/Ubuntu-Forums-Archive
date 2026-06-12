---
title: "Creating custom Keyboard Shortcut problem"
date: 2011-02-27
forum: General Help
---

### Post by holadebob on 2011-02-27
I'd like to open a directory with the F12 key. I haven't any problem getting Keyboard Shortcuts to run programs, but cannot figure out how to have it open a directory.

I tried making a link to the directory and using that, but still no go. Edit: The directory I want opens when I use its link

Can't find anything on the net for this. Most just mention that we can create custom keyboard shortcuts. :)

I tried using /home/directory/directorydesired, but no go. Edit: The directory I want opens when I use the link

Problem stupidly simple, but haven't stumbled on it yet.

Thank you

---

### Post by cjhabs on 2011-02-27
Map the F12 key to:

nautilus --browser folder_path

---

### Post by holadebob on 2011-02-28
I used 
nautilus --/home/dir/dir

and assigned it to F12, 

Don't get error, don't get any response...

Must be something basic I'm not seeing.

---

### Post by cjhabs on 2011-02-28
> **holadebob said:**
> I used 
nautilus --/home/dir/dir

and assigned it to F12, 

Don't get error, don't get any response...

Must be something basic I'm not seeing.

The syntax is as I had above:
nautilus --browser foldername
NOT
nautilus --foldername

You may need the full path to nautilus also - /usr/bin

---

