---
title: "Grep is making me go crazy! Why won't it work right?"
date: 2009-11-04
forum: General Help
---

### Post by rob86 on 2009-11-04
I've been trying to use grep for at least 20 minutes now trying to do something simple and it just doesn't seem to be working . It's most likely something I'm doing wrong, but I can't figure it out.

I have old msn chat logs on my other hard drive. I want to simply use grep to search for a particular string/word. First of all, I am in the correct directory with the logs which MSN stores in html format.

It seems simple enough, grep -i 'string' *.html

But I've tried with futility to get this to work.I've tried using a string 'hello' and other common words, and it NEVER find anything. I thought something weird was going on after a while,  so I opened up one of the logs in gedit, and saved an exact duplicate (named Fakelog)  in the same folder.

Strangely, enough grep could find matches in this new copy, but not in the original?

I thought this was weird, so I did "file *" and had this output
```

April 2008.html:      XML document text
August 2007.html:     XML document text
August 2008.html:     XML document text
August 2009.html:     XML document text
December 2007.html:   XML document text
December 2008.html:   XML document text
February 2008.html:   XML document text
Fakelog 2005.html: ASCII text
```As you can see, it seems to be calling my Fakelog an Ascii test, and every other file an XML text. I wonder if this is why grep won't work on the original log files?

Can someone help me understand the logic behind this seemingly illogical problem? I can't understand it. I can cat the .html logs and they output , but grep just won't work on them.


Edit:

It doesn't seem to be the file type really, I'm still trying to make sense of this, and I tried this:
```
$ tail -2 October\ 2007.html  <----- printing the last two lines of a log
</html> <--- it worked
$ tail -2 October\ 2007.html | grep html <--- this didn't work
$ echo '</html>' | grep html <-- this did
</html>
$ 
```It doesn't work when I 'tail', but it does when I echo the same thing?  I don't get it. I noticed that the last line of the file is seemingly blank and I can't remove the blank line. I wonder if that's causing problems, really I have no idea.

---

### Post by mbeach on 2009-11-04
any chance you could attach a small sample of the file obviously without all the details of your chat history.

edit:
nevermind, as that would probably involve resaving, thus ending up with a searchable copy.

second edit:
okay, found a similar file but was able to use grep to search it without issue. I'd suspect you may have a permissions issue. Are the files on your ubuntu box, or mounted from another location?

if instead of opening in gedit, you use cp to create a duplicate, do you see the same behaviour?

what if you try something like:
```

sed '$d' oneOfYourFilesWithBlankLastLine.html | grep SomeStringLikeHello

```
the sed '$d' should delete that last line (not permanently)

---

