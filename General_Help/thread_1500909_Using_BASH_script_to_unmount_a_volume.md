---
title: "Using BASH script to unmount a volume"
date: 2010-06-03
forum: General Help
---

### Post by Broussard on 2010-06-03
Hello, 

As part of a script for imaging floppy disks on a Mac, I am trying to unmount the volume located at /dev/disk1

In my script I put--
#!/bin/sh
echo "This should unmount the external floppy drive."
sudo umount /dev/disk1
--

But I get an error-- 
[FONT=Courier New]umount: /dev/disk1\r[/FONT]: not currently mounted
--

I also tried excluding the "sudo" with the same result. Any ideas where the [FONT=Courier New]"\r"[/FONT] is coming from or what else might be the problem?

[FONT=Courier New]sudo umount /dev/disk1[/FONT] works when I use it in the command line, but as a long term solution I need it in my script if possible.

---

### Post by bodhi.zazen on 2010-06-03
My guess is you wrote the script on Windows ?

[http://www.cyberciti.biz/faq/howto-unix-linux-convert-dos-newlines-cr-lf-unix-text-format/](http://www.cyberciti.biz/faq/howto-unix-linux-convert-dos-newlines-cr-lf-unix-text-format/)

---

### Post by quadproc on 2010-06-03
> **Broussard said:**
> 
But I get an error-- 
[FONT=Courier New]umount: /dev/disk1\r[/FONT]: not currently mounted
--

The \r is a representation of the RETURN (ENTER) character.  Linux and Unix do not use that character to indicate an end of line; instead, Linux uses NEWLINE (line feed) which is represented as \n in many contexts.

Try editing your script by dleting the offending line and replacing it with a line which you end with the ENTER key.  If you are using a Linux editor then the ENTER character will become a newline in your file and everything should work.

quadproc

---

### Post by daamaya1982 on 2010-06-03
Try running dos2unix on the script and see if that works... If you vi the file, you should see ^M at the end, and this represents CR-LF.

---

### Post by Broussard on 2010-06-07
Ah, yes I believe I did write it on a Windows station and fixing the new line solved the problem. 

Thanks all.

---

