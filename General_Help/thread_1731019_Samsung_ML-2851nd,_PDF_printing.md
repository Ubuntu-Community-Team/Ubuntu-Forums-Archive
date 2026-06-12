---
title: "Samsung ML-2851nd, PDF printing"
date: 2011-04-16
forum: General Help
---

### Post by holadebob on 2011-04-16
I have not been able to print out Getting Started with Ubuntu 10.04, a 4.4Mb PDF file. It will print out 9 pages in one job, but any more and the printer light blinks for a while and then the printer rejects the job, clearing the queue.

10 pages of this PDF file is around 3 Mb, and there is about 28Mb memory available in the printer buffer.

Although the printer ran out of the box with Ubuntu(perfectly), I decided to download and install the most recent driver from Samsung(because it was there),which hiccupped and responded slowly, so I deleted that driver and went back to Ubuntu default Cups drivers for ML-2850 series.

I have 1 Gb of system memory and cannot figure out where to focus the troubleshooting = the printer memory, or my driver installation, or my system ram (1Gb).

The printer runs perfectly otherwise.

Thank you busy folks

Any thoughts?

---

### Post by holadebob on 2011-04-18
No one has this problem or has any ideas?

---

### Post by Zill on 2011-04-18
holadebob:  I have a Samsung ML-4500 printer which generally runs fine on my all-linux network using the standard Ubuntu/cups driver.

The only thing it has trouble with is large PDF files, generally containing colour, or detailed images such as Google Maps.  Then it just hangs blinking (although my printer queue does not clear automatically).

I not sure exactly where my problem is but am not too concerned as I don't need to print much really - I aspire to run a paperless office ;-)

If you have access to a Windows or Mac PC then I suggest you try your printer on that and see if it prints the PDF file OK.  If so then it looks like the printer hardware and buffer is adequate and the problem *may* be with the Linux driver.

If the PDF file will not print using another host PC then maybe the printer is not really up to the task :-(

---

### Post by holadebob on 2011-04-18
Thanks, Zill.

Books in English are very difficult to get here, so we download and print them out (small print, 4 pages a sheet duplex) for reading at leisure. I haven't had any problems printing >100 pages of regular word or txt docs, no hesitation at all. But only being able to print 9 pages of PDF seems a bit confining. 

I can increase the memory in the printer from 28M to 156Mb, but I'm not clear if that will help, cause I don't know what the printer uses the memory for, is it for solely cache? I thought the processing of the print files was done by the drivers installed in cups?

Am I right, or am I going down the wrong road?

---

### Post by Zill on 2011-04-19
> **holadebob said:**
> ...Am I right, or am I going down the wrong road?
Sorry but I don't know much about memory management :-(  Maybe someone more knowledgeable about this will be able to assist.

Are you unable to try the printer on another PC/OS as I suggested earlier?  This would help to narrow down the problem.

---

### Post by holadebob on 2011-04-19
I sure agree with you and would like to, but it will take a while - when we go to town (once a month), I'll ask the folks at the internet cafe if they'll let me install it there. None of my neighbors have a computer. 

I'll get back to you in a couple of weeks
Thanks

---

