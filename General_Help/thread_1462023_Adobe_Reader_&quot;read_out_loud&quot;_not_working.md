---
title: "Adobe Reader &quot;read out loud&quot; not working"
date: 2010-04-25
forum: General Help
---

### Post by megahost on 2010-04-25
I have just installed Adobe reader, looking into its Read Out Loud plug-in. I have selected to activate the reader, and it creates a box around the text. Whenever i click on text, i can move the box, but it doesn't read to me. I'm thinking it's because Ubuntu doesn't come with a virtual output device. Can anyone tell me what I need to do?

Thanks
MegaHost

---

### Post by Chronon on 2010-04-25
Do you have a working text-to-speech engine?  
[QUOTE=http://help.adobe.com/en_US/Reader/8.0/help.html?content=WS58a04a822e3e50102bd615109794195ff-7d15.html]
Read a PDF with Read Out Loud
Note: The Read Out Loud feature is available for Linux but not for other versions of UNIX.

The Read Out Loud feature reads aloud the text in a PDF, including the text in comments and alternate text descriptions for images and fillable fields. In tagged PDFs, content is read in the order in which it appears in the document’s logical structure tree. In untagged documents, the reading order is inferred, unless a reading order has been specified in the Reading preferences.

Read Out Loud uses the available voices installed on your system. If you have SAPI 4 or SAPI 5 voices installed from text-to-speech or language applications, you can choose them to read your PDFs.[/QUOTE]

---

### Post by megahost on 2010-04-25
I have festival on my machine. When I tried to listen to it, I still get no sound. So I tried to make festival my default TTS. I still have nothing.

---

### Post by hawaiian1der on 2010-04-27
I have the same problem.

---

### Post by crxz0193 on 2013-03-26
> **hawaiian1der said:**
> I have the same problem.

I know thread is outdated but since i landed on this page "the feel lucky factor".

Adding solution: [https://help.ubuntu.com/community/AcrobatHowTo](https://help.ubuntu.com/community/AcrobatHowTo)

[h=2]Enabling Read Out Loud[/h] Adobe Reader has the ability to read text from PDF files out loud to the user.  

To enable Read Out Loud in Ubuntu please install the libgnome-speech7 package then run at the Terminal: 

sudo /var/lib/dpkg/info/acroread.postinst configure 

Open the desired PDF file and click View -> Read Out Loud -> Activate Read Out loud -> View -> Read Out Loud 

and then choose either Read This Page Only or Read to End of Document. 

Read Out Loud preferences are found by clicking Edit -> Preferences -> Reading

thanks
czar
p.s. my keay board seems to be printing 'R' instead of the letter capital 'r' don't know the reason.

---

### Post by wildmanne39 on 2013-03-26
Thread closed. Please do not post in old threads.

---

