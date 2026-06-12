---
title: "SSH issues etc..."
date: 2012-02-18
forum: General Help
---

### Post by ServerSwag on 2012-02-18
Hello all, 
I used to have a perfectly fine machine operating ubuntu server before I tried to use it as a time machine for my mac. That went over fine but now I want to use it for hosting webpages again. I think everything is fine for now but the current issue is my ssh. I used to be able to use cyberduck with little or no problem but today when I tried to edit one of my pages and error showed up that read,
```

SSH Error: Upload failed

Permission denied (SSH_FX_PERMISSION_DENIED: The user does not have sufficient permissions to perform the operation.).

```

I have no idea whats wrong. I have done numerous google searches and came up with really nothing useful. please help!!

---

### Post by HermanAB on 2012-02-18
It doesn't seem to be a SSH problem as such.  Have a look at the user, groupand MAC settings of the directory that you are trying to upload to.

---

### Post by ServerSwag on 2012-02-19
So how do I do that?

---

### Post by ServerSwag on 2012-02-19
I figured out all I can do is copy the original file and make a new 1 with the same name and code and I'm fine

---

### Post by Iowan on 2012-02-19
Check **ls -al** on the directory containing the two files to see if there's a permission difference.

---

