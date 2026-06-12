---
title: "Contents of several files linked into a single file"
date: 2010-11-17
forum: General Help
---

### Post by Birion on 2010-11-17
Hi,

I realise this is probably a futile question, but is there a way to link (not cat) several files into one?

e.g.

File A contains "Hello World".
File B contains "Goodbye World".
Linked file C contains "Hello World\nGoodbye World".
And changing A to "Hello Dolly" would also change C to "Hello Dolly\nGoodbye World".

---

### Post by a-user on 2010-11-17
well, the answer is yes... and no.

no, there is no direct way to accomplish this,. i don't know everything but i am quite sure about that.

BUT, with daemon / a programm running in the background you can do scuh things.
you culd have a program that opens a filesocket (say file_s) and simply waits for read requests on that socket.

so when another programm opens file "file_s" for reading and starts reading, our background programm starts writing the content of your two files.
additionally your background program should react on changes in the files you want concatinated.

this simple solution would only permit sequential reading. to also be able seek within your "total file" there is more work to do.

but you got the idea...

---

### Post by Birion on 2010-11-17
Hmm, I quite figured that, but was hoping someone with more experience might prove me wrong. Well, your suggestion sounds a bit too complicated to me, I guess I'll just set up some script to cat them all into an ordinary file. I was just hoping to avoid the middle step, since I'm bound to spend half an hour compiling and recompiling with no changes before I realise I should update the source file. Just annoying. But thanks anyway.

---

