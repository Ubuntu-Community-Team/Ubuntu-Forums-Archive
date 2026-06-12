---
title: "Can't open *.pdf file"
date: 2012-01-03
forum: General Help
---

### Post by quickk on 2012-01-03
I am having exactly the same problem.   I have this fancy pdf file with embedded forms and such, but can't open it with any linux pdf viewers.  

To make the situation even more annoying, installing acroread is broken.  On Kubuntu 11.10 64bit I get the following message:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 acroread : Depends: nspluginwrapper but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

The when I try to install I get more of the same:

```
The following packages have unmet dependencies:
 nspluginwrapper : Depends: nspluginviewer (= 1.4.4-0ubuntu3)
E: Unable to correct problems, you have held broken packages.

```

Anyway, the problem I think is that acroread is 32 bit, and won't install on a 11.10 64 bit system (worked fine on every other version of Ubuntu/Kubuntu I've used).  

The only way to open my pdf document is to use a virtual machine, but then I can't print from it :(

---

### Post by oldos2er on 2012-01-03
Post moved to its own thread.

---

### Post by Anstice on 2012-01-03
Have you really tried all pdf viewers?

You could try opening it in xournal. I know it is intended for editing pdfs but I have had trouble opening some pdfs before and have found that using xournal I was able to open them. 

As long as you ignore the editing tools at the top it will work just the same as any pdf viewer. Just make sure if you do annotate it to save the file as .pdf.xoj as it needs both the source pdf file and the annotated version.

---

### Post by quickk on 2012-01-04
oldos2er:  why was my post moved to its own thread?   I realize that the other thread was quite old, but it is one of the top google search results for this problem.   The problem still exists, but now my reply does not have any context.

Anstice:  Thank you for the suggestion.   I've tried all the pdf viewers that I can think of and none work.   I just tried xournal now, and it does not work either.  

The pdf file that I am trying to open is [at this link.]("http://research.mtroyal.ca/documents/ethics/hreb_application_v1.2.pdf")

---

### Post by bluexrider on 2012-01-04
> **quickk said:**
> oldos2er:  why was my post moved to its own thread?   I realize that the other thread was quite old, but it is one of the top google search results for this problem.   The problem still exists, but now my reply does not have any context.

Anstice:  Thank you for the suggestion.   I've tried all the pdf viewers that I can think of and none work.   I just tried xournal now, and it does not work either.  

The pdf file that I am trying to open is [at this link.]("http://research.mtroyal.ca/documents/ethics/hreb_application_v1.2.pdf")
I just tried your link and I can not open it either. Could it be the link has no data?

---

### Post by bluexrider on 2012-01-04
I think it is a problem with the web site because I can view other .PDF pages from [http://research.mtroyal.ca/documents/ethics/](http://research.mtroyal.ca/documents/ethics/)

---

### Post by fdrake on 2012-01-04
i can open it but it says this message:

from "file hreb_application_v1.2.pdf" you have
> 
hreb_application_v1.2.pdf:                        PDF document, version 1.7


in the web page the file is 555kb just like my file:
> 
555K 2012-01-04 14:07 hreb_application_v1.2.pdf


so I think there is nothing wron with your pdf reader.

---

### Post by Anstice on 2012-01-04
I downloaded Adobe's Linux reader from the link below and it opened perfectly.

[ftp://ftp.adobe.com/pub/adobe/reader/unix/9.x/9.4.6/enu/](ftp://ftp.adobe.com/pub/adobe/reader/unix/9.x/9.4.6/enu/)

---

### Post by quickk on 2012-01-05
> I downloaded Adobe's Linux reader from the link below and it opened perfectly.


Thanks Anstice!   Now, the only problem is that I can't seem to get the adobe reader installed...   (To everyone else: while the file opens with linux pdf readers like evince and okular, you only get the "Please wait..." message.  To get the real file, it seems like you need acrobat.)

---

### Post by Anstice on 2012-01-05
I just downloaded the deb file and it opened it in Ubuntu Software Centre.
You could try download it and run it with:

```
sudo dpkg -i "adobereader_enu".deb
```

replacing the text in the quotes with the package name.

---

### Post by Jerry N on 2012-01-05
Interesting - this is the first time I have seen a PDF file that could only be opened by Acrobat.  I installed the Adobe Acrobat reader from the repositories in Mint 11 (based on Ubuntu 11.04) and it reads perfectly.

Jerry

---

### Post by oldos2er on 2012-01-05
> **quickk said:**
> oldos2er:  why was my post moved to its own thread?  

From the forum posting guidelines: "If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

### Post by bluexrider on 2012-01-05
> **Anstice said:**
> I downloaded Adobe's Linux reader from the link below and it opened perfectly.

[ftp://ftp.adobe.com/pub/adobe/reader/unix/9.x/9.4.6/enu/](ftp://ftp.adobe.com/pub/adobe/reader/unix/9.x/9.4.6/enu/)

Interesting! I did the same thing. I could not load the OP link until I installed the linux reader.

Thanks

---

