---
title: "Get block of text from a file"
date: 2011-08-12
forum: General Help
---

### Post by Kissell on 2011-08-12
Sorry, but I can't figure this out myself.  I tried using "sed" but just couldn't get it to work.  

Say I have a file called "myfile" and it contains this text:
> 
        </tr> <tr bgcolor="#FFFFFF"><th colspan="7" height="4"></th></tr><tr bgcolor="#FFFFFF" onmouseover="this.bgColor='#FFFF99'" onmouseout="this.bgColor='#FFFFFF'"><th width="60%" align="left">           <table cellspacing="0" cellpadding="0" border="0" width="100%"><tr><th align="left" class="label"><a href="http://dl.mysite.org/link/43583f8315ba1c9b7bcad39be7ba4f267fd10dcaa933/file.zip" rel="nofollow"><img src="/images/down.gif" border="0"></a>


I want to wget a website and grab the latest http linked file through a script.  There are often multiple http links per file, but the one I want is always the first instance of a link to the site dl.mysite.org, and it's filename is always file.zip.

So I want to grab a middle block of text in the file, everything starting at the first instance of "http://dl.mysite.org" and ending at the first instance of "file.zip".  

I tried "sed" but had no luck.  Can anyone help, please?

](*,)

---

### Post by TeoBigusGeekus on 2011-08-12
Something like
```
sed -i 's/http\:\/\/dl\.mysite\.org/\nhttp\:\/\/dl\.mysite\.org/g' myfile
sed -i 's/file\.zip/file\.zip\n/g' myfile
wget $(grep http://dl.mysite.org myfile)
```

---

### Post by Kissell on 2011-08-12
hmmm...  whatever that is doing...  it works, a little too well.  

I don't understand, the sed commands seem to be modifying "myfile" so that grep can act upon it...  but when I go look at "myfile" it seems unedited.

Anyway, it downloads all the links on the page that point to a file.zip on dl.mysite.org.

But, I'm only interested in the first link.  Its wasting a lot of bandwidth grabbing the others just so I can delete them.  :lolflag:

---

### Post by Kissell on 2011-08-12
> **TeoBigusGeekus said:**
> Something like
```
sed -i 's/http\:\/\/dl\.mysite\.org/\nhttp\:\/\/dl\.mysite\.org/g' myfile
sed -i 's/file\.zip/file\.zip\n/g' myfile
wget $(grep http://dl.mysite.org myfile)
```

I modified it to use -m 1, to only get the first match...  now it's perfect!! 
> wget $(grep -m 1 [http://dl.mysite.org](http://dl.mysite.org) myfile)

Thanks a lot, you're a rock star!
:guitar:

---

### Post by TeoBigusGeekus on 2011-08-12
You're welcome.
The script finds the text "http://mysite.org" and puts a new line in front of it (all instances).
It then finds the text "file.zip" and puts a new line at its end (all instances again).
Thus, the wanted address is isolated and easily used with a grep command; -m 1 for the first instance as you already noticed.

---

### Post by Kissell on 2011-08-12
yeah, I see that now...  cool.  I thought maybe my original attempts weren't working was because the text was crammed in there with no line breaks or spaces, should have tried that.

but every solution yields several more questions...  I noticed wget would download the files and name them file.zip, file.zip.1, file.zip.2

That naming convention isn't to my liking, we have lots of windows clients that rely on file extensions...  I'll go look at the man page for wget, maybe I can easily change the naming convention of downloads?  My first thought was assigning a name, but that doesn't work, because then subsequent downloads would be overwritten or skipped...  no...  I want to modify the naming convention for autonaming, so it does something like file.zip, file.1.zip, file.2.zip, leaving the extension on the end where it belongs.  Do you happen to know how to do that off the top of your head?

---

### Post by Kissell on 2011-08-12
I just ended up setting the grep result as a variable and then doing an expression on that to get part of the download link as a unique name...  then used the -O parameter of wget.  

So each file gets a specfic name, derived from the unique link.

okay, back to work.

---

