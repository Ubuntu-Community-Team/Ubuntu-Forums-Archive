---
title: "Stuck in low res"
date: 2011-01-08
forum: General Help
---

### Post by WisJim on 2011-01-08
A follow-up to another thread I posted to when I should have created a new thread.


Hi realzippy,
  

Here's what happened.  I read your post again and I tried copying and pasting your xorg.conf into mine.  When I rebooted it came back even worse.  The icon blocks and the fonts were double the size of what they were before.  And they were already in a VGA mode.  So I restored my backup copy.  It was about that time that I made the post to the thread about low res mode.   
  

As a reminder here's what I wrote:
 “I have a similar problem - stuck in low res in Ubuntu. I run a quad boot system (Vista, UStudio 10.1, CAE 8.04, and Ubuntu 10.1). All are loaded in their own partitions. Ubuntu is the only one with the low res problem. I updated my xorg.conf using the settings you suggested with no luck. 
A couple of Questions: 1. If I delete the xorg.conf does it recreate itself during the reboot process? 2. Can I delete it using the command line. 3. With 10.1 running for two systems is there a conflict I need to watch out for? 
Thanks”
  

What I really did was to compare the xorg.conf file you posted and the one that was on my system then change the parts that were different.  This did nothing.  I then replaced the contents of my file with the contents of the one you posted.  That's when it came back bigger than ever.
  

While I was waiting for your reply I got to thinking what's the worst that could happen.  I would have to open a shell and restore the back-up copy again.  So I deleted the xorg.conf file and rebooted.  The worst happened – the x-window never appeared but I could log in as a root user.  I had some other things come up and I couldn't play with it at the time so I rebooted into the Ustudio system and took care of what I had to do there.  Ustudio usually starts in low res mode, gives me a warning then opens a window that lets me restart the xwindow and it works fine from there on out.  When I rebooted after that to restore the xorg.conf file in Ubuntu it booted normally into the hi-res mode I was looking to restore.
  

Long answer short – it seems I had to reboot twice to get the Ubuntu xwindow to see the new xorg.conf file and recreate the old settings and now everything's back to where it was.  I still don't know if booting into UStudio affected the settings.

  

I rarely have to post a question because inevitably someone else has had the same problem and the answer is already there.  And with a little bit of effort (read 'search engine') it can be found.
  

Thanks So Much to everyone in this user's group for all the help over the years!

---

