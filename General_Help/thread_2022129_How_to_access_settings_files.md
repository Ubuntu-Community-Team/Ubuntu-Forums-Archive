---
title: "How to access settings files"
date: 2012-07-10
forum: General Help
---

### Post by paul1149 on 2012-07-10
Newbie here.

I'm trying to access some settings files for Opera, which I believe are in /home/paul/.opera/operaprefs.ini.

But Nautilus is not listing any [COLOR="darkred"].<*****>[/COLOR] folders under home. And if I [COLOR="DarkRed"]sudo nautilus[/COLOR] the result, while it doesn't list the bookmarks in the left pane, still does not show the [COLOR="darkred"].<****>[/COLOR] folders. In fact it even shows fewer things under the home directory.

So how does one access these folders?

Thanks.

---

### Post by SlugSlug on 2012-07-10
> **paul1149 said:**
> Newbie here.

I'm trying to access some settings files for Opera, which I believe are in /home/paul/.opera/operaprefs.ini.

But Nautilus is not listing any [COLOR=darkred].<*****>[/COLOR] folders under home. And if I [COLOR=DarkRed]sudo nautilus[/COLOR] the result, while it doesn't list the bookmarks in the left pane, still does not show the [COLOR=darkred].<****>[/COLOR] folders. In fact it even shows fewer things under the home directory.

So how does one access these folders?

Thanks.


press Ctrl+h  :)

---

### Post by paul1149 on 2012-07-10
Dang, that wasn't too difficult. No one ever accused me of being a fast learner!

Thanks much, 
p.

---

### Post by lukeiamyourfather on 2012-07-10
> **SlugSlug said:**
> press Ctrl+h  :)

To elaborate on that, anything that starts with a period is a hidden file.

---

### Post by Neill_R on 2012-07-10
FYI

when you 

sudo nautilus 

or better still

gksu nautilus&

& means spawn nautilus and return to terminal 

you become root therefore you must navigate to your home folder 
/home/paul

in terminal after edit

ls -lt /home/paul/folder_you_save_in 

should see files are owned  by paul an not root 
if not 

sudo chown paul:paul /home/paul/folder/file

---

### Post by paul1149 on 2012-07-11
Thank you, Luke and Neill. I was aware of that, but not that specific command line.

---

