---
title: "auth.log CRON question"
date: 2011-01-10
forum: General Help
---

### Post by baddnady23 on 2011-01-10
Lately I have been receiving this in my auth.log file.  It seems to be repeating over and over, and I didn't know if was anything normal or something I should be worried about...


```
Jan 10 05:17:01 andrew-server CRON[5365]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 10 05:17:01 andrew-server CRON[5365]: pam_unix(cron:session): session closed for user root
Jan 10 05:39:01 andrew-server CRON[5373]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 10 05:39:01 andrew-server CRON[5373]: pam_unix(cron:session): session closed for user root
Jan 10 06:09:01 andrew-server CRON[5387]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 10 06:09:01 andrew-server CRON[5387]: pam_unix(cron:session): session closed for user root
Jan 10 06:17:01 andrew-server CRON[5399]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 10 06:17:01 andrew-server CRON[5399]: pam_unix(cron:session): session closed for user root
Jan 10 06:25:01 andrew-server CRON[5405]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 10 06:25:01 andrew-server CRON[5405]: pam_unix(cron:session): session closed for user root
Jan 10 06:39:01 andrew-server CRON[5412]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 10 06:39:01 andrew-server CRON[5412]: pam_unix(cron:session): session closed for user root
Jan 10 07:09:01 andrew-server CRON[5426]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 10 07:09:01 andrew-server CRON[5426]: pam_unix(cron:session): session closed for user root
Jan 10 07:17:01 andrew-server CRON[5441]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 10 07:17:01 andrew-server CRON[5441]: pam_unix(cron:session): session closed for user root
Jan 10 07:30:01 andrew-server CRON[5552]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 10 07:30:01 andrew-server CRON[5552]: pam_unix(cron:session): session closed for user root
Jan 10 07:39:01 andrew-server CRON[5676]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 10 07:39:01 andrew-server CRON[5676]: pam_unix(cron:session): session closed for user root
Jan 10 08:09:01 andrew-server CRON[5895]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 10 08:09:01 andrew-server CRON[5895]: pam_unix(cron:session): session closed for user root

```

---

### Post by NuxIT on 2011-05-13
I'm trying to figure this activity out as well. I'm not sure what this auth.log activity is from??:confused: I logged out of the workstation at 14:00 today and came back at 17:00 and logged in. So, I'm not exactly sure what these sessions are from?? I wasn't using the station at all during these 3 hours so it seems strange. Appreciate any feedback. 

```
May 13 14:17:01 brits CRON[3715]: pam_unix(cron:session): session opened for user root by (uid=0)
May 13 14:17:01 brits CRON[3715]: pam_unix(cron:session): session closed for user root
May 13 14:39:01 brits CRON[3725]: pam_unix(cron:session): session opened for user root by (uid=0)
May 13 14:39:01 brits CRON[3725]: pam_unix(cron:session): session closed for user root
May 13 15:09:01 brits CRON[3741]: pam_unix(cron:session): session opened for user root by (uid=0)
May 13 15:09:01 brits CRON[3741]: pam_unix(cron:session): session closed for user root
May 13 15:17:01 brits CRON[3751]: pam_unix(cron:session): session opened for user root by (uid=0)
May 13 15:17:01 brits CRON[3751]: pam_unix(cron:session): session closed for user root
May 13 15:39:01 brits CRON[3761]: pam_unix(cron:session): session opened for user root by (uid=0)
May 13 15:39:01 brits CRON[3761]: pam_unix(cron:session): session closed for user root
May 13 16:09:01 brits CRON[3777]: pam_unix(cron:session): session opened for user root by (uid=0)
May 13 16:09:01 brits CRON[3777]: pam_unix(cron:session): session closed for user root
May 13 16:17:01 brits CRON[3787]: pam_unix(cron:session): session opened for user root by (uid=0)
May 13 16:17:01 brits CRON[3787]: pam_unix(cron:session): session closed for user root
May 13 16:39:01 brits CRON[3797]: pam_unix(cron:session): session opened for user root by (uid=0)
May 13 16:39:01 brits CRON[3797]: pam_unix(cron:session): session closed for user root

```

---

