---
title: "Text to speec software"
date: 2010-06-29
forum: General Help
---

### Post by s1mp13m4n on 2010-06-29
Hello everyone.  I am visually impaired and about to go back to college.  I will be getting my textbooks in a digital format on a cd-rom to read from the computer.  I was also told of this Windows software called Neospeech from the college.  I do not use Windows and that is $100 software anyway.  What is out there that will take text or .doc files and covert them to speech or .mp3 files that will work on Ubuntu 10.04 and/or Fedora 12?  The Ubuntu machine is 32bit and the Fedora 12 machine is 64bit.  Thank you for the help.

---

### Post by KeyserSoze93 on 2010-06-29
Espeak comes with Ubuntu and does a pretty decent job.

Simply put your text in a plaintext file and run:

```

espeak < file.txt

```

Espeak has many parameters for adjusting the voice and accent, which can help to make it sound less like a computer.

There are other solutions too, such as Festival and Ksayit, however espeak is a good default and worth a try.

---

### Post by s1mp13m4n on 2010-06-29
OK I added the GUI for Espeak and it does work but sounds like a computer.  So how do I get human sounding speak from it?  I looked at the Sourceforge page but only saw the main program files.  :)

---

### Post by KeyserSoze93 on 2010-10-01
> **s1mp13m4n said:**
> OK I added the GUI for Espeak and it does work but sounds like a computer.  So how do I get human sounding speak from it?  I looked at the Sourceforge page but only saw the main program files.  :)

"Espeak has many parameters for adjusting the voice and accent, which can help to make it sound less like a computer."

See the man page

---

