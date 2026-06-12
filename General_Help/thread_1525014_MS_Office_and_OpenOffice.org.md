---
title: "MS Office and OpenOffice.org"
date: 2010-07-06
forum: General Help
---

### Post by skarme on 2010-07-06
I'm using Ubuntu 10.04 and I frequently use OpenOffice.org for doing my college work, such as typing out reports and making presentations. However when I open the files I make in MS Word(2007) or MS Powerpoint (2007) [on some other PC], the alignment of the text, etc changes. It happens the other way round too, files created using MS Office tools aren't displayed as intended in OpenOffice. It is pretty vexing sorting out text. Is there any way that I can avoid doing this?
I'm primarily concerned with text and presentation files.

---

### Post by arubislander on 2010-07-06
In what format are you saving the files? MS Office 2007's ODF support is poor at best. And so is OpenOffice.org support of OpenXML. I've found that if I save the text files in Word 97 the text displays correctly unless I have some advanced formatting in place.

Presentations are a more difficult matter...

---

### Post by skarme on 2010-07-06
> **arubislander said:**
> In what format are you saving the files? MS Office 2007's ODF support is poor at best. And so is OpenOffice.org support of OpenXML. I've found that if I save the text files in Word 97 the text displays correctly unless I have some advanced formatting in place.
 
Presentations are a more difficult matter...
 
Well the files I create in college are in docx format. When I open them in my PC with OpenOffice, the alignment is messed up. I don't really use advanced formatted, pretty much the basic features. On the other hand, I've created both .doc and .odt text files using OpenOffice, and both don't display as intended on MS Office. I generally complete my stuff at home and take print outs, however ocasionally I need to use MS Office in college to complete my work and that's where my problems begin with resorting, especially for large files.

---

### Post by arubislander on 2010-07-06
Steer clear of docx if you want to open files in both MS Office and OpenOffice.org.

You should understand that OpenOffice.org's implementation of doc(x) format is the result of reverse engineering and is bound to be feature incomplete. If you need full MS Office compatibility you should try running MS Office with Wine on Ubuntu...

On the other hand, if access to your documents from both places is the sole requirement, maybe you could try a web based solution like Google Docs and their ilk.

---

### Post by skarme on 2010-07-06
> **arubislander said:**
> Steer clear of docx if you want to open files in both MS Office and OpenOffice.org.
 
You should understand that OpenOffice.org's implementation of doc(x) format is the result of reverse engineering and is bound to be flawed. If you need full MS Office compatibility you should try running MS Office with Wine on Ubuntu...
 
On the other hand, if access to your documents from both places is the sole requirement, maybe you could try a web based solution like Google Docs and their ilk.
 I should have mentioned that I have saved documents in both .doc and .docx formats. However I got your point. Thanks for the sugestion, I'll definately check out Google Docs. 
One question: Whats the reason for such weirdness, I mean files created using Open Source softwares should run flawlessly on others, that was the general perception in my mind, correct me, if I'm wrong.

---

### Post by arubislander on 2010-07-06
> **skarme said:**
> I should have mentioned that I have saved documents in both .doc and .docx formats. 
You did mention it. My experience with .doc format has always been one way: From MS Office to OpenOffice.org. And personaly I've never experienced any extreme weirdness, but the files have mostly been single page documents. And it might have helped that I also installed the msttcore fonts package.

> One question: Whats the reason for such weirdness, I mean files created using Open Source softwares should run flawlessly on others, that was the general perception in my mind, correct me, if I'm wrong.
There is a difference between Open Source and Open Standards. File Formats can be Open Standards or not. The software that implements the formats can be Open Source or not.

Open Document Format (ODF) is an open standard, meaning that the description of the format is available to anyone who cares to look into it, making it possible for anyone to write the documents to a file in the format correctly and to read files created in the format correctly. Notice I said, it makes this possible. Differences in interpretation, sloppy programming or cutting corners can all cause files written by one program to be misinterpreted by another program. But at least such problems could be solved, especially if the programs are Open Source, because then more people can potentially pitch in.

While Office Open XML (OOXML) is also an ISO standard, and as such an Open Standard, the software that implements the standard (MS Office 2008 / 2010) is not. And since how MS Office implements it is the defacto reference implementation, however Microsoft implements OOXML will be the standard, irrespective of what the documentation says. But because MS Office is not Open Source, it is not easy to see how Microsoft has done it's implementation, and so increase compatibility.

In short when an Open Source application is seeking to be compatible with a Closed Source application, even if it is with Open Standards, there will always be incompatibility issues, more so, if the standards or applications or both are relatively new.

Hope this helps... a bit.

---

### Post by gradinaruvasile on 2010-07-06
Google docs is not better than OpenOffice at document compatibility - it is worse because it kinda axes many formattings. It also doesnt have much features but only the basic ones. But its free, so try it see if it fits your needs.

The latest version of OpenOffice is 3.2.1 (maybe it has better document compatibility) - i think 10.04 has 3.2.0 by default - try the new one, look for it in PPAs or download from the site (but if you download it from the site, you will have to remove some of the installed OpenOffice packages before installing it).

---

### Post by fetuspuppet on 2010-07-06
See if you have any friends in the military... Office is $30 bucks for them.

---

### Post by skarme on 2010-07-06
> **arubislander said:**
> In short when an Open Source application is seeking to be compatible with a Closed Source application, even if it is with Open Standards, there will always be incompatibility issues, more so, if the standards or applications or both are relatively new.
Well that was all I could understand. haha
The rest was beyond my knowledge. That was just a general question and I got the answer. Thanks.
Single page documents have no issue in virtually any format. It is the long ones. For examples when a topic which should start from page 5, starts from page 4. Things similar to this, mainly issues with the text moving out of desired position (the order of the document remains, however).

---

### Post by skarme on 2010-07-06
@[[SIZE=5][COLOR=#000000]gradinaruvasile[/COLOR][/SIZE]]("http://ubuntuforums.org/member.php?u=589640") 
yes i did check the website out. I'll install it as soon as possible and provide feeback. Appreciate your response.

---

### Post by brown12 on 2010-07-06
> **skarme said:**
> I'm using Ubuntu 10.04 and I frequently use OpenOffice.org for doing my college work, such as typing out reports and making presentations. However when I open the files I make in MS Word(2007) or MS Powerpoint (2007) [on some other PC], the alignment of the text, etc changes. It happens the other way round too, files created using MS Office tools aren't displayed as intended in OpenOffice. It is pretty vexing sorting out text. Is there any way that I can avoid doing this?
I'm primarily concerned with text and presentation files.

There are many reasons this can happen even in *.doc format. Some of the formatting marks, such as bullets, use graphical or typographical symbols that don't translate properly from OpenOffice to MS Word and back. 

Styles are another important reason that paragraphs can render differently. Paragraph styles hold information about margins, tabs, fonts, line spacing, and lots of other things. Styles are not implemented the same way in OpenOffice as in MS Word.

Saying that OpenOffice is compatible with *.doc means that you can open, edit, and save *.doc format with OpenOffice, but it doesn't mean that the documents are going to look the same in both packages. 

If you need to collaborate with MS Word users, OpenOffice will let you make edits, track changes, and insert comments, but you can't get publication-quality results from a document that has gone back and forth between the two. Check out the OOo user docs, forums, and wiki for more information.

---

### Post by arubislander on 2010-07-06
> **gradinaruvasile said:**
> Google docs is not better than OpenOffice at document compatibility - it is worse because it kinda axes many formattings. It also doesnt have much features but only the basic ones. But its free, so try it see if it fits your needs.


The idea was not for Google Docs to replace either MS Office or OpenOffice.org. It was to avoid having to switch apps in between locations. If one set of tools is available at both locations and is used at both, gone are the compatibility issues.

I was assuming a browser and internet access would be available at school as well as at home.

---

### Post by BigCityCat on 2010-07-06
You know you can use Microsoft Office Live online for free with a hotmail account. 25 gigs free space for your documents. I'm pretty sure this could solve your formatting issue.

> With a Windows Live SkyDrive account you can:

    *
      Store and share documents from virtually anywhere
    *
      ***View and edit documents using Microsoft Office Web Apps***
    *
      Take advantage of upto 25 GB of storage

[http://www.officelive.com/en-us/](http://www.officelive.com/en-us/)

---

### Post by skarme on 2010-07-06
> **brown12 said:**
> There are many reasons this can happen even in *.doc format. Some of the formatting marks, such as bullets, use graphical or typographical symbols that don't translate properly from OpenOffice to MS Word and back. 
 
Styles are another important reason that paragraphs can render differently. Paragraph styles hold information about margins, tabs, fonts, line spacing, and lots of other things. Styles are not implemented the same way in OpenOffice as in MS Word.
 
Saying that OpenOffice is compatible with *.doc means that you can open, edit, and save *.doc format with OpenOffice, but it doesn't mean that the documents are going to look the same in both packages. 
 
If you need to collaborate with MS Word users, OpenOffice will let you make edits, track changes, and insert comments, but you can't get publication-quality results from a document that has gone back and forth between the two. Check out the OOo user docs, forums, and wiki for more information.
 Well your spot on. These are the kind of problems I face usually. Opening and editing documents isn't an issue. It is just the look of the document changes when viewed in repective word processors. I wish OpenOffice could work around with this. However the suggestions on this forum promise to be helpful. :p

---

### Post by skarme on 2010-07-06
> **BigCityCat said:**
> You know you can use Microsoft Office Live online for free with a hotmail account. 25 gigs free space for your documents. I'm pretty sure this could solve your formatting issue.
 
 
[http://www.officelive.com/en-us/](http://www.officelive.com/en-us/)
Thankyou. The only issue is that not all labs in college are connected to the internet.

---

### Post by arubislander on 2010-07-07
> **skarme said:**
> Thankyou. The only issue is that not all labs in college are connected to the internet.

Then Google Docs will not be an option either.

---

### Post by arubislander on 2010-07-07
> **skarme said:**
> It is just the look of the document changes when viewed in repective word processors. I wish OpenOffice could work around with this.

For reasons already posted, there will always be these kinds of issues. But having said that. I've found lately that a Powerpoint 2003 file renders more faithful to the original in OpenOffice.org Impress than in PowerpointViewer for Linux, which uses Wine. Go figure...

---

### Post by quinnten83 on 2010-07-07
you could go the other way around.
Use Open Office for everything.
You can run open office from a USB stick, you can download that here: [www.portableapps.com]("www.portableapps.com")

---

### Post by skarme on 2010-07-07
> **quinnten83 said:**
> you could go the other way around.
Use Open Office for everything.
You can run open office from a USB stick, you can download that here: [www.portableapps.com]("www.portableapps.com")

Awesome!
This is exactly what I'll do. Thanks a lot.

---

