---
title: "Chromium: &quot;always open files of this type&quot; unavailable"
date: 2010-11-24
forum: General Help
---

### Post by reve_etrange on 2010-11-24
I am using the Chromium daily beta PPA, fresh upgrade, build 8.0.552.208 (66581) Ubuntu 10.10.

When I download a file, the download bar menu option to "Always open files of this type" is grayed out.  Clicking the file icon, or its link in the Downloads tab opens the file using the preferred application for that file type.  I.e., I can download and open a PDF in Chromium but I can't instruct it to open PDFs every time.  Clearing auto-opening preferences has no effect.

Anyone know if this is a configuration error?  Otherwise I must write a bug report...

---

### Post by anac0nda on 2010-12-04
I'm using Chrome stable with Ubuntu 10.04. Today, I upgraded to Chrome 8.0.552.215. I also used to auto-open PDF files with Acrobat Readed, but now this option is disabled for PDF files.

Also, in the web applications we developed we used to serve PDF files with content-disposition: inline, and chrome showed them in embedded Acrobat. Now Chrome forces their own PDF viewer, but it lacks one major feature - print button! I know that I can click on the wrench button and print from there, but some of our users are not tech-savvy and will be confused.

---

### Post by evencoil on 2010-12-05
I have this same problem: I used to auto-open pdfs in evince. Since updating, they now open in google's internal reader. If I turn off the google pdf viewer plugin (about:plugins) then the option to open a pdf in an external viewer is greyed out. Anyone have a work around?

---

### Post by Bluejade on 2010-12-06
Same here. Up until updating today, Chrome opened PDFs in Evince. Now, the "Always open files of this type" checkbox is greyed out, and it prompts me to save every PDF.

---

### Post by Bluejade on 2010-12-06
After a little googling, and some reading between the lines, it seems that Google has deemed PDFs too dangerous to allow them to be automatically opened:
[http://blogs.pcmag.com/securitywatch/2010/06/google_chrome_to_add_native_pd.php](http://blogs.pcmag.com/securitywatch/2010/06/google_chrome_to_add_native_pd.php)
[http://news.cnet.com/8301-30685_3-20024520-264.html](http://news.cnet.com/8301-30685_3-20024520-264.html)

So it seems this isn't a bug, it's a "feature".

---

### Post by negatifzeo on 2010-12-07
This is INCREDIBLY annoying. There has to be a hack or  workaround to get this back to the way it was, right?

---

### Post by evencoil on 2010-12-14
New updates in the past few days and this didn't change. Any ideas on a workaround?

---

### Post by Francewhoa on 2011-02-16
That's a pain ;) Google said this issue will be fix in the next stable release. Solution to auto-open pdf at [http://ubuntuforums.org/showpost.php?p=10466012&postcount=26](http://ubuntuforums.org/showpost.php?p=10466012&postcount=26)

---

