---
title: "Emesene video chat."
date: 2009-11-01
forum: General Help
---

### Post by bhishan on 2009-11-01
When I try to use video chat in emesene it gives a error saying no libmimic. I typed sudo apt-get install libmimic in terminal and it says package doesnt exist. What should I do?

---

### Post by scouser73 on 2009-11-01
Go to Synaptic Package Manager and search for it there, perhaps you might strike it lucky that way.

---

### Post by kostkon on 2009-11-01
Is [*libmimic0*]("http://packages.ubuntu.com/karmic/libmimic0") the package you are looking for?

---

### Post by bhishan on 2009-11-01
> **kostkon said:**
> Is [*libmimic0*]("http://packages.ubuntu.com/karmic/libmimic0") the package you are looking for?

libmimic0 is already installed, emesene says it needs libmimic

---

### Post by dc740 on 2009-11-01
I tried it and restarted emesene... but it keeps saying libmimic is not installed. weird

EDIT:

I fixed it. the package that it's needed to make emesene webcam work is:

python-libmimic

doh... It was so obvious. I can't believe I lost 15 minutes searching for an answer.

Thanks to everyone. I hope this helps:

> sudo apt-get install libmimic0 python-libmimic

and that's it. restart emesene and you are ready to go :)

---

### Post by bhishan on 2009-11-02
> **dc740 said:**
> I tried it and restarted emesene... but it keeps saying libmimic is not installed. weird

EDIT:

I fixed it. the package that it's needed to make emesene webcam work is:

python-libmimic

doh... It was so obvious. I can't believe I lost 15 minutes searching for an answer.

Thanks to everyone. I hope this helps:



and that's it. restart emesene and you are ready to go :)

I installed python-libmimic and I can only see a blank window, i cant see the video

---

### Post by bhishan on 2009-11-06
help

---

### Post by Neo40 on 2009-11-07
If I go to Options-->Preferences-->Webcam, it says select the webcam you want to use...
Well, I don't see any choices available?!! 
I know my webcam is working (it works fine with "cheese" or "amsn".

Any idea I could try?
Thanks

---

### Post by bhishan on 2009-11-08
I think i will just use amsn.

---

