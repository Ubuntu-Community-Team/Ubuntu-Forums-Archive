---
title: "Climate change -BBC"
date: 2006-02-14
forum: General Help
---

### Post by zubrug on 2006-02-14
The BBC is looking for help setting up a network of personal computers in an attempt to accurately monitor climate change. [http://www.bbc.co.uk/sn/hottopics/climatechange/aboutexperiment1.shtml](http://www.bbc.co.uk/sn/hottopics/climatechange/aboutexperiment1.shtml)  I am interested in participating in this program. They have a linux download (sh), has anyone attempted this. 
I have only recently graduated from Linspire to Ubuntu and would require some advise regarding installing this.
My kids and yours would appreciate this.

---

### Post by shamrock_uk on 2006-02-14
After seeing your reply, I just installed it. You have nothing to worry about - it's done in a snap. 

Simply click the linux download link. Head to a terminal and cd to the download folder. 

type sh and hit <tab> 

to autocomplete the name and run the script. Then navigate into the created folder and simply do 

./run_client or ./run_manager depending whether you want a gui. 

It seems to be working for me, but the gui looks a bit...rushed. That could be my slightly bizarre theme though.

---

### Post by zubrug on 2006-02-14
Thanks, you rock

---

### Post by dolphinholmer on 2006-02-15
I've not managed success with this on my breezy box.
I've had it running twice and both times, after an hour or so of running fine, the client has terninated with this:

SIGSEGV: segmentation violationStack trace (4 frames):
./boinc[0x8087046]
[0xffffe420]
./boinc[0x807afd1]
[0x31303735]

I think this has something to do with memory use but am not sure. Any ideas?

---

