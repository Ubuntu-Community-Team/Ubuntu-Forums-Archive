---
title: "problem with aget!!! please help"
date: 2010-10-25
forum: General Help
---

### Post by dymond on 2010-10-25
i have installed aget 0.4-6 on my new ubuntu 10.10
and i have the following error

aget [http://www.google.com](http://www.google.com)
Error: Cannot get hostname from URL...

i have a proxy server
but

wget [http://www.google.com](http://www.google.com)
--2010-10-25 18:03:37--  [http://www.google.com/](http://www.google.com/)
Connecting to 10.1.8.31:8080... connected.
Proxy request sent, awaiting response... 302 Moved Temporarily
Location: [http://www.google.co.in/](http://www.google.co.in/) [following]
--2010-10-25 18:03:37--  [http://www.google.co.in/](http://www.google.co.in/)
Connecting to 10.1.8.31:8080... connected.
Proxy request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html'

    [ <=>                                   ] 9,585       --.-K/s   in 0.03s   

2010-10-25 18:03:37 (333 KB/s) - `index.html' saved [9585]

works fine!!!

what is the problem with aget??
also i need aget since my isp has limit on the download file size i.e. i cant download files greater than 50mb, but i can download as many files i want of less than 50mb
please help!!!

---

