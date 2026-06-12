---
title: "Why can't I pipe into the 'file' command?"
date: 2010-05-09
forum: General Help
---

### Post by tjw09003 on 2010-05-09
I'm looking for an mp3 file in the firefox cache folder.

I was thinking I could run the command 'find -size +2M' and pipe that output into the 'file' command to tell me which is an mp3, something like this

find -size +2M | file     

But this doesn't work, what am I doing wrong?

This is output 
Usage: file [-bcikLhnNrsvz0] [-e test] [-f namefile] [-F separator] [-m magicfiles] file...
       file -C -m magicfiles
Try `file --help' for more information.

---

### Post by cogier on 2010-05-09
You "Pipe" the output of one command into another command. You can't "Pipe" to a file you need to redirect - Use **>** instead of **|**.

---

### Post by kaibob on 2010-05-09
I don't believe the file command accepts standard input. It should work with xargs. For example:

> $ ls
testfile.txt

$ echo testfile.txt | file
Usage: file [-bcikLhnNrsvz0] [-e test] [-f namefile] [-F separator] [-m magicfiles] file...
       file -C -m magicfiles
Try `file --help' for more information.

$ echo testfile.txt | xargs file
testfile.txt: ASCII English text


BTW, I believe there will be a problem if a filename contains spaces. This can be gotten around as follows:

```
find . -print0 | xargs -0 file
```

---

### Post by blueridgedog on 2010-05-09
"file" is used to determine the type of a file.  I suspect you want the results of the find command to go "into" a file.  In that case it would be:

```
find -size +2M > filenameyouselect
```

Change the filenameyouselect to be the name of the file you want the create and place the results in.  If the file you want to use already exists and you want to append the output of the command to the file, use >> in place of >.

---

### Post by tjw09003 on 2010-05-09
@kaibob, Thanks for the help. That's what I needed.

@Cogier and @blueridgedog, NO lol, but thanks for trying. I needed the file types not putting the output in a file.

---

### Post by jhuuht9 on 2012-12-16
I have extracted two histograms from this file:

Bin/signal/HWW_41_lord_cteq66m_170_170_sig_LO.dat

which contained a lot of other histograms. Now I'm trying to plot them, but I'm not sure how to do it? 

Also it says that the extracted files are in ASCII English text format, could someone tell me what that  means and whether it is possible to plot them?

---

### Post by overdrank on 2012-12-16
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

