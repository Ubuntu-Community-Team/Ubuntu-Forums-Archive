---
title: "unable to download mp3s using chrome 18.0.1025.168"
date: 2012-05-13
forum: General Help
---

### Post by newbuntuxx on 2012-05-13
I am unable to download mp3 files using google chrome version 18.0.1025.168. I am using ubuntu 10.04. The file that I tried to download is:
[http://www.qoranway.com/maqamat/nahawand1/37.mp3](http://www.qoranway.com/maqamat/nahawand1/37.mp3)

There are other mp3 files on that page (nahawand.html) and in that site (qoranway.com) that I also can't download using google chrome. I am able to download the files using wget:

wget [http://www.qoranway.com/maqamat/nahawand1/37.mp3](http://www.qoranway.com/maqamat/nahawand1/37.mp3)
--2012-05-13 23:42:57--  [http://www.qoranway.com/maqamat/nahawand1/37.mp3](http://www.qoranway.com/maqamat/nahawand1/37.mp3)
Resolving [www.qoranway.com](www.qoranway.com)... 74.208.61.110
Connecting to [www.qoranway.com|74.208.61.110|:80](www.qoranway.com|74.208.61.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 810342 (791K) [application/octet-stream]
Saving to: `37.mp3'

100%[================================================================================================================================>] 810,342     1.04M/s   in 0.7s    

2012-05-13 23:42:58 (1.04 MB/s) - `37.mp3' saved [810342/810342]

I am also able to download the mp3 files using: firefox 12.0. 

Note that I am able to download those mp3 files using chrome 18.0.1025.168 on Windows 7. The problem appears to be with the ubuntu version of chrome.

Anyone have any ideas as to why this is happening? Or is it simply a chrome bug?

---

