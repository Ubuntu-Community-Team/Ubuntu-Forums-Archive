---
title: "How Do Bash Files Work?"
date: 2011-03-17
forum: General Help
---

### Post by khoraski on 2011-03-17
I don't get it, I looked it up and apparently .sh files are Bash Files. 

But when I put in codes and run the file, they don't work.

Such as:

```
echo hello > /home/jason/Desktop/test.txt
```

Am I using the wrong file? Or am I missing something?

---

### Post by blueridgedog on 2011-03-17
The first thing you need in the file is a note as to what shell to use:

Such as:


```
#!/bin/bash
echo hello > /home/jason/Desktop/test.txt
```

Then you need to make the file executable:

```
chmod u+x /path/to/your/file.sh
```

Then you can run it:

```
/path/to/your/file.sh
```

---

### Post by user1397 on 2011-03-17
> **khoraski said:**
> I don't get it, I looked it up and apparently .sh files are Bash Files. 

But when I put in codes and run the file, they don't work.

Such as:

```
echo hello > /home/jason/Desktop/test.txt
```

Am I using the wrong file? Or am I missing something?
if you put that code in a file called "test.sh" and then run **./test.sh** in the terminal, it should work.  If it says permission denied, it just means that the file is not set to be executable.  You can either change that in the properties of that file with your mouse, or you can do a quick **chmod +x test.sh**

---

### Post by khoraski on 2011-03-17
> **blueridgedog said:**
> The first thing you need in the file is a note as to what shell to use:

Such as:


```
#!/bin/bash
echo hello > /home/jason/Desktop/test.txt
```

Then you need to make the file executable:

```
chmod u+x /path/to/your/file.sh
```

Then you can run it:

```
/path/to/your/file.sh
```

Thanks! :D
Every question I ask here gets answered. I love this place.

---

### Post by Lorin Ricker on 2011-03-18
Learning to do bash scripting well and the right way is "*a Big Topic*"... While I applaud and encourage your experimentation, I'd also recommend that you get ahold of a good book on the topic, either at Amazon or at your local public library.  Here's a good one (and yes, there are lots more):

**[Learning the Bash Shell]("http://oreilly.com/catalog/9781565923478")** -- Cameron Newham & Bill Rosenblatt, O'Reilly, ISBN 978-0-596-00965-6

Good luck, and happy bashing...

---

### Post by seawolf167 on 2011-03-18
[Here ]("http://mywiki.wooledge.org/BashGuide")is a good guide to learning bash scripting

---

### Post by Lorin Ricker on 2011-03-18
Yes, this is a very good guide -- I'd not seen it before, but I've bookmarked it now!  Tx!

---

