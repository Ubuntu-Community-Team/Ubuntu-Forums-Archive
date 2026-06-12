---
title: "Where are my services?"
date: 2010-07-05
forum: General Help
---

### Post by breadpoker on 2010-07-05
I have 10.04 LTS, 64-bit server edition of Ubuntu. 

I installed LAMP, SSH, and MAIL server during the initial install. I haven't done much else to the server.

I know for a fact that cron is starting on bootup (among others) [(see screenshot)]("http://www.flickr.com/photos/51847218@N08/4764157871/lightbox/")

[IMG]http://farm5.static.flickr.com/4099/4764157871_3090107aed_z.jpg[/IMG]

I also see that running "sysv-rc-conf" shows that its *NOT * set to start on boot. [(see screenshot)]("http://www.flickr.com/photos/51847218@N08/4764794260/in/photostream/lightbox/"). I also see this reflected in /etc/rc.2/

[IMG]http://farm5.static.flickr.com/4077/4764794260_2c969281a5_z.jpg[/IMG]

So I ask - whats up with that? What would happen if I checked a service to start on boot that is already running? Would it double-start? Would doing that mess anything up? Why is this mismatched with whats actually starting? Why wouldn't LAMP show up in startup scripts - or email - or cron - for that matter on a default Ubuntu install?

I miss the old days of BSD style startup scripts, damn it. If whats actually starting doesnt reflect the SYS-V startup scripts, then what use are they? Seriously. What is the correct way to manage system start-up scripts in Ubuntu?

And more importantly - How would I go about disabling a service that is starting automatically (like mysql) but isn't set to start in the startup scripts?

---

### Post by sisco311 on 2010-07-05
Ubuntu uses Upstart. Unfortunately some of the services are still managed using the System-V style init scripts.

To manage the services managed by Upstart jobs you have to edit the job files(/etc/init) manually. 

[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

---

