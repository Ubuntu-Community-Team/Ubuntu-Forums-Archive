---
title: "Audio in PDFs"
date: 2011-01-20
forum: General Help
---

### Post by clruwe on 2011-01-20
Hi there! For about three months I've been going up and down the internet looking for a solution to this problem... Basically I take this distance learning course. Every lesson is sent to me via email in PDF format and it includes many audio examples which are embedded in the file. The problem is none of the Ubuntu readers seem to recognize it, and the Adobe reader says I need a plug-in which does not exist for my system. I quote: "We're sorry, but the third-party media player  required to play the selected media file in your Adobe PDF document  isn't available for your system". I've been taking this course for two years and I still have two more to go. I contacted the company that sells this course and they were as puzzled as I am... Is there a way to extract the audio from the PDF? Or alternatively open it with another application? I would hate to have to go back to windows for this one issue...

Thank you very much for any help!

C.

---

### Post by dcottingham on 2011-01-20
Never seen a pdf with audio in it -- but the first thing that comes to mind is to try pdftk with the unpack_files option and see what happens.

You can get pdftk with apt-get or other software getter, and you can read more about it at pdflabs.com.

---

### Post by dcottingham on 2011-01-22
I have bad news and possible good news. I managed to find one example of a PDF with embedded audio, and with it I verified that the method I just suggested -- using pdftk -- doesn't work. That's the bad news. The possible good news is that I found

[http://yhager.com/content/extracting-embedded-audio-pdf](http://yhager.com/content/extracting-embedded-audio-pdf)

which gives a method for extracting audio, video, and what have you. The following caveats apply: 1. you have to compile a little utility that you download from that page -- it explains how, 2. from a stock ubuntu distro I believe you'll have to install some software to be able to compile anything -- "sudo apt-get gcc" will probably do the trick. I realize this is probably not what you wanted to hear.

Another thing you probably didn't want to hear is that this method actually didn't work on the one and only embedded audio PDF file I've found. I managed to successfully extract the audio from the file using emacs, but that's not a method that sane people would want to try.

Still, if you're desperate enough, I think the method outlined on that web page is worth trying. If it works, it works.

---

### Post by clruwe on 2011-02-04
You're right! That is not what I wanted to hear... But I will most definitely give it a try, thanks!

---

### Post by Jboulden on 2012-08-27
Guys,

I followed the instructions contained on that linked website and was unable to extract the video (realize you were talking about Audio).  Just kept getting syntax errors on the script.  Could be that the file is bad -- but I don't think so.  It plays just fine in a Windows machine.

I'm including the error messages that I'm getting.

./pdf_extract_embedded.c: line 17: syntax error near unexpected token `('
./pdf_extract_embedded.c: line 17: `void* bin_strstr(void* haystack, int hlen, void* needle, int nlen) {'

---

