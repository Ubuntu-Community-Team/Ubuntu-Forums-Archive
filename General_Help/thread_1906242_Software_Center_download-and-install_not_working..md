---
title: "Software Center download-and-install not working."
date: 2012-01-08
forum: General Help
---

### Post by the big e on 2012-01-08
Trouble using the Software Center.
I get error messages instead of the handy one-click install.

The last thing I installed was Skype, which I did via their own web page rather than through the Software Center. Is is possible that installing something this way screwed up the Software Center's settings? What's the cure?

Error messages are first: one that says the internet connection doesn't work (even though I checked and my connection is actually good) and then one that says it doesn't trust the source.

---

### Post by the big e on 2012-01-08
p s The update manager has a similar problem. Both software center and update manager no longer ask me for a password prompt either.

---

### Post by bluexrider on 2012-01-08
go to the 'Software Sources' open and under the 'Download From' select 'main server' then 'other' choose 'best server'. Select best server and wait for the update. choose server and close. 

then in terminal

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by the big e on 2012-01-09
Thank you, I tried what you said and it worked. I installed a small application to test it and I think we are back to normal again. I don't understand precisely what I did, though.

Was that command line a thing that updated everything?

What could I have done that screwed up my settings in the first place?

p. s. my browser just told me it has been updated.

---

