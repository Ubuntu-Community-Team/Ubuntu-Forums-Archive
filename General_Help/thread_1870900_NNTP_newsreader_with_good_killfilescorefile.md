---
title: "NNTP newsreader with good killfile/scorefile"
date: 2011-10-28
forum: General Help
---

### Post by Acharn on 2011-10-28
In the "good old days" we called it a killfile, which was how we implemented <plonk>. In trying to find one now I get the idea they are now called scorefiles because you have to do something called scoring. OK, as long as I can use it to not ever see posts from certain obnoxious people.

My requirement seems simple to me. I want to be able to kill (or score) posts that come from a particular IP address. That's found in a header named "nntp-posting-host." When I was reading usenet on Windows many years ago, there was a free program calle Forte Free Agent. It didn't have a killfile at all, but there was a separate program called Nfilter that you could set up to filter the stream before it got to Free Agent. Later Forte stopped distributing Free Agent and I had to use Agent for a while and then I stopped reading usenet news for a while and now I'm using Ubuntu 11.04, and I think I should be able to find better newsreaders than I could on Windows.

So can anyone point me to a newsreader that has this feature? From what I've been able to find with Google, it appears that slrn can do this IF the newsfeeder gives that header, but it might be a little difficult. It looks like Pan won't. It looks like none of the other newsreaders based on  a GUI will. I'm surprised. What was easily done in 1976 can't be done now?

Can anyone tell me a newsreader that has this capability? Oh, and regular expressions, too, of course.

---

### Post by Lars Noodén on 2011-10-28
I used to use [tin](http://manpages.ubuntu.com/manpages/oneiric/en/man1/tin.1.html) a lot.  It's been many years now, but I think it has what you are looking for.

---

### Post by Acharn on 2011-10-28
> **Lars Noodén said:**
> I used to use [tin](http://manpages.ubuntu.com/manpages/oneiric/en/man1/tin.1.html) a lot.  It's been many years now, but I think it has what you are looking for.

Ah. It's available in the Software Center. I'll give it a try. I'm hoping one of the newer ones with a pretty GUI will fill the bill. I'm sorry to say many years of using Windows has spoiled me. Now that I've moved to Ubuntu I have to regain/improve my CLI skills. I'm trying to learn EMACS, too. I think it includes a newsreader.:)

---

### Post by Lars Noodén on 2011-10-28
I tried a half dozen pretty GUI-based ones, back in the day, and always found tin better.  However, there might be better ones available nowadays, but AFAIK my ISP does not even offer Usenet anymore nor do many others so work on Usenet clients is going to be minimal.  

IMHO the microblogging sites are just trying to recreate a centralized version of Usenet.  

Write back when you have found a newsreader that does what you need.

---

### Post by andrew.46 on 2011-10-30
> **Acharn said:**
> So can anyone point me to a newsreader that has this feature? From what I've been able to find with Google, it appears that slrn can do this IF the newsfeeder gives that header, but it might be a little difficult. 

I hope that I have made slrn a little easier for Ubuntu users by writing and maintaining this page:

slrn Community Ubuntu Documentation
[https://help.ubuntu.com/community/slrn](https://help.ubuntu.com/community/slrn)

Details of utilising scoring can be found here but a great source of further usage can be found by querying news.software.readers when you get online.

---

### Post by Acharn on 2011-10-30
Yeah, I found that page earlier and would like to thank you for it. I think I might try slrn next. tin is a real blast from the past. I'm trying to work through the man page now, and it's daunting. tin spends about ten minutes at the beginning of the session, apparently reading the groups file from the server. The free server I'm using claims to offer 1Mb/sec, but I don't think it's that fast. Also, after doing a catchup on the newsgroup I'm most interested in, after a day there are no new messages, so the news feed may not carry that newsgroup -- or only have limited access. I think the server is mostly for people interested in binaries anyway, which is not what I'm interested in -- but it's free. I really enjoyed usenet from about 1998 to 2004, but my favorite group was taken over by trolls who stayed, and I lost interest.

---

### Post by andrew.46 on 2011-10-30
You may find that slrn has a similar vintage to tin BTW :). An old but good starter guide for tin is here:

How to Use Tin Newsreader
[http://www.hkbu.edu.hk/~itsc/infonote/howto/usenet.html](http://www.hkbu.edu.hk/~itsc/infonote/howto/usenet.html)

This page recommended by the current tin developer...

---

### Post by dcstar on 2011-10-31
> **Acharn said:**
> 
.........
So can anyone point me to a newsreader that has this feature? From what I've been able to find with Google, it appears that slrn can do this IF the newsfeeder gives that header, but it might be a little difficult. It looks like Pan won't. It looks like none of the other newsreaders based on  a GUI will. I'm surprised. What was easily done in 1976 can't be done now?

Can anyone tell me a newsreader that has this capability? Oh, and regular expressions, too, of course.

Maybe Pan does:

[http://www.mail-archive.com/pan-users@nongnu.org/msg07664.html](http://www.mail-archive.com/pan-users@nongnu.org/msg07664.html)

---

### Post by Acharn on 2011-10-31
Oh, thanks. That tutorial is very helpful. I don't know, though. I tried to fire up tin today and after it spent 15 minuted "Reading groups from file" I gave up and killed the process. My Internet connection is not as reliable as I would like, and the widespread floods this last month have not helped. My ISP claims to deliver 6Mb/sec, and the free news server claims to deliver 1 Mb/sec, but my download speeds lately have been more like 12-14KB/sec. I've been getting acquainted with EMACS recently and there is a module called gnus which I might try.

---

### Post by Acharn on 2011-10-31
> **dcstar said:**
> Maybe Pan does:

[http://www.mail-archive.com/pan-users@nongnu.org/msg07664.html](http://www.mail-archive.com/pan-users@nongnu.org/msg07664.html)

Great! Just the kind of explanation I wanted. Thanks ever so much.

I'm going to mark this thread SOLVED now. Thank you to all who posted here. You really helped me a lot.:D

---

### Post by Oadbylad on 2011-11-01
Mornin....:) my very first post after just trying Ubuntu....ive read the above thread and found it vey informative ....for which i that you all....
My question is its ok getting a newsreader but how would i post on usnet i cant seem to find any software
Thanks

---

### Post by dcstar on 2011-11-01
> **Oadbylad said:**
> Mornin....:) my very first post after just trying Ubuntu....ive read the above thread and found it vey informative ....for which i that you all....
My question is its ok getting a newsreader but how would i post on usnet i cant seem to find any software
Thanks

[LIST=1]
[*]Don't hijack threads - ask a new question.
[*]All Newsreaders post.
[/LIST]

---

