---
title: "wget help"
date: 2009-10-01
forum: General Help
---

### Post by americano70e10 on 2009-10-01
Hey guys, I'm trying to get used to using wget to download files. For learning purposes I'm trying download a karmic-koala iso file from the server but when the download finishes the image size is over 1Gb. The command that I'm using is ```
wget -c http://cdimage.ubuntu.com/daily/current/karmic-alternate-amd64.iso

```.
I'm pretty new at using wget so I might be missing an option or something. Can anyone tell me what I'm missing? I've searched around and so far nothing.
Any help will be appreciated.

Thanks in advance.

---

### Post by mac9416 on 2009-10-01
Hey,

I noticed you are using "-c". That causes Wget to "continue" an already-started download. That works fine if the file on the server remains unchanged, but if the file changes on the server, you will end up with a garbled file (and likely an oversized file). In the words of the Wget man page:

> ...if the file is bigger on the server because it's been
changed, as opposed to just appended to, you'll end up with a
garbled file.  Wget has no way of verifying that the local file is
really a valid prefix of the remote file.

You are downloading the daily build of Karmic, which, of course, changes daily. I would suggest beginning a new download and overwriting the old one with this command:

```
$ wget http://cdimage.ubuntu.com/daily/current/karmic-alternate-amd64.iso
```

Hope that helps!

---

### Post by americano70e10 on 2009-10-01
Oh.. I see.. Didn't think that was the case. I thought that the daily build was the most recent one, but didn't think it changed every day.
Thanks for the insight.

---

### Post by americano70e10 on 2009-10-01
Ops.. Double posted =P

---

