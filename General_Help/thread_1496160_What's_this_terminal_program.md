---
title: "What's this terminal program?"
date: 2010-05-28
forum: General Help
---

### Post by cat^_^ on 2010-05-28
Atleast I think it's a terminal program...

I remember several years ago while using Redhat 7 when working in the terminal it would automatically complete the pathnames and filenames for you..

If I was typing in the terminal "cd downloads" but I only typed "cd do" it would automatically complete my command with "cd documents"  but if I continued to type "cd dow" it would know that I don't mean the documents folder and it would know the only other folder path with a dow in it is downloads.  I'm not sure if my description is 100% accurate but I think you get the idea.

Ubuntu doesn't seem to have this by default and I'm curious if I can get it.  Is it a terminal program/client I need to use, or just an option?  I don't know what it's called so I've had a hard time googling for it!  Thanks for your help!

---

### Post by bananas4370 on 2010-05-28
> **cat^_^ said:**
> Atleast I think it's a terminal program...

I remember several years ago while using Redhat 7 when working in the terminal it would automatically complete the pathnames and filenames for you..

If I was typing in the terminal "cd downloads" but I only typed "cd do" it would automatically complete my command with "cd documents"  but if I continued to type "cd dow" it would know that I don't mean the documents folder and it would know the only other folder path with a dow in it is downloads.  I'm not sure if my description is 100% accurate but I think you get the idea.

Ubuntu doesn't seem to have this by default and I'm curious if I can get it.  Is it a terminal program/client I need to use, or just an option?  I don't know what it's called so I've had a hard time googling for it!  Thanks for your help!

You'll need to install bash-completion

sudo apt-get install bash-completion

Hope that helps

---

### Post by cat^_^ on 2010-05-29
Ahh Thanks!

---

### Post by jobix on 2010-05-29
Perhaps you already know this, but tab completion also works in this case. You type "cd do" and press the TAB key and it completes it for you.

---

