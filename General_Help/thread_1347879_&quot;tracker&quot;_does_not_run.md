---
title: "&quot;tracker&quot; does not run?"
date: 2009-12-06
forum: General Help
---

### Post by b00n on 2009-12-06
I would like to try Ubuntu's file system indexing/search feature "tracker" under *System > Preferences > Search and Indexing*.  I brought that up and clicked "Enable Indexing" (this is a laptop) but unclicked the Power Management disables, so it should always run.  When I do "top" I see nothing consuming significant resources, the disk is not spinning, and "ps" shows nothing with "track" in the name running.  If I run *tracker-search-tool* manually I get "cannot connect to search service, as it may be busy."  I see nothing notable in /var/log/syslog.  I do not have a ~/.Tracker, hence no log file.  /etc/xdg/autostart/trackerd.desktop does not contain "Hidden", so it should be enabled.  When I run /usr/lib/tracker/trackerd -v=1 manually it seems to run (still waiting to see if it completes without errors, it will be a while).  This is a laptop, but I unclicked the power management stuff, and 'acpi" reports I am on mains power anyway.

I'd like it to run automagically, though, rather than running it manually.

I looked in these forums and found nothing to help.  I also looked at

[https://wiki.ubuntu.com/Tracker](https://wiki.ubuntu.com/Tracker)

Any suggestions about how to figure out why it does not run automatically?  Thanks.

BTW, despite the problems other folks have reported with trackerd clobbering their CPU, etc., I see it making very low use and the system remains responsive.  I have the indexing speed set way down.  Oh, and this is Ubuntu 9.10 on an x86-32 laptop.

---

