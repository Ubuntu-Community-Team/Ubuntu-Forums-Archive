---
title: "Recovery: TXT, TEX, or DVI files overwritten on NTFS partition"
date: 2012-01-23
forum: General Help
---

### Post by collud2 on 2012-01-23
Well, hello Forums! I've gotten myself into a fun situation to describe:
I lost an eighth of my undergraduate research report by accidentally deleting overwriting the original file instead of the backup.  

I run Ubuntu and Windows off separate partitions (ext3 and NTFS, rsp) on the same physical drive.  The file extension is .tex, but is essentially a text file with markup.  I exported it to .dvi format every so often, so that's also something I could live with recovering.  I used gedit to write, but by the time I realized it had been deleted, the automatic gedit backup was gone.
The file was saved to and being edited on the NTFS partition, which I quickly remounted as read-only.  

I've tried the [grep -a "keywords" /dev/disk > output] method, but am not sure I can do this while still using the same physical disk... it seems to get interrupted. 

Can anyone provide the format for DVI recovery (or plaintext!) to use with Scalpel or a similar tool?  Or, just plain HELP?

---

### Post by xyzzyman on 2012-01-23
Alot of us have been in your situation for one reason or another (Mostly stupidity. I've gotten frustrated and cancelled an NTFS resizing, and a long time ago I typed a G instead of an H and placed an ext2 file system over an NTFS after being awake for 48 hours).

Mounting as read-only was VERY smart. In my personal experience I'd recommend using photorec first, and I think most people here on the forums would use it as their first line tool.

[http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec](http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec)

A good tutorial for all of them is at: 

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

Halfway down the page it begins with how to use photorec, and then it shows how to use scalpel. Photorec alot of the work is done for you, especially since TEX is one of the main formats it can search for, where scalpel needs more hand holding.

Do you have a guesstimate of the file size? Being a text file with latex formatting I'm assuming it's much smaller than a similiar word document. Which is a good thing as less chance of it being fragmented.

---

### Post by collud2 on 2012-01-23
PhotoRec has already made my good side - it collects and backs up the files it finds as it works; scalpel and grep seemed to avoid doing anything until they each had trouble - "error reading disk" or "input/output error".  But PhotoRec also seems to hit  *major* lag point about 12 minutes in.  :-/ 
 I'm doing the full-on USB recovery test, now - hoping the trouble is from simultaneous hardware access.  Thanks for the pointer!
Oh - the file is just under 30 kb. So, unlikely to get fragmented, but almost nothing to spot in a search.  It seems so strange for such a small file to be so important ... I suppose this is what computing was like thirty years ago...

---

### Post by collud2 on 2012-01-27
In update, I tried PhotoRec, Scalpel, ... it seems I'm either not patient enough to sit through a scan of a 200GB partition (likely), or my disk has some corrupted sector on it that keeps bringing the scans to a standstill about 20 minutes in (also likely).  I decided to just rewrite the content I lost.  I'll know it's not the same, and will be sure I've forgotten something, but only I'll know that.  
Thanks for the help!

---

