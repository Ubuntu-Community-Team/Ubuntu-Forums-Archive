---
title: "CUPS Page Log Weirdness"
date: 2009-10-30
forum: General Help
---

### Post by dbsoundman on 2009-10-30
I seem to be having some strange issues with my CUPS page log. I've set up some cron jobs that save the page log statistics to a separate logfile every hour so that I can collect print info for the users of my printer. I just installed this printer on the computer, so there was only one print job listed in the page_log, from the test page printed from my roommate's computer when we added the printer to his computer. Tonight, I was doing some testing and printed a couple of pages to see if they showed up in the log. At first, they showed up in the online interface page log, but not in the page_log at /var/logs/cups/page_log. Then, I also noticed that the printer was fouling up the print jobs, so I restarted the computer it was attached to. Now, the print jobs that I had from tonight have disappeared from the online page log as well. I guess my question is where did they go, and will they reappear? I should note that I'm on Ubuntu but my roommate is on Windows Vista. Also, one thing I noticed is that my print jobs show up in my local computer's page_log, just not the print server's page_log where they should be (at least as I understood it).

Thanks,
Dan

---

