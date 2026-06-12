---
title: "recommendations for small office server sought"
date: 2011-04-13
forum: General Help
---

### Post by dave37 on 2011-04-13
Hi,

I am looking for recommendations for expanding our small office server.  Our current setup is as follows:

no domain, simple peer based network. 1 server, IBM netvista running Ubuntu 8.04 as a samba file server, 1 os drive, 1 data drive, 1 backup server HP dx5150 running 8.04. 1 os drive, 1 data drive. IBM backs up hourly to HP using rsync to allow for quick local server failure recovery. IBM backs up nightly to offsite rsync server for disaster recovery. 5 windows xp workstations using intensive accounting software that accesses the files on the IBM.  Clients have been complaining of slow net speeds during periods of heavy load. Both servers have the maximum possible RAM.

What we want to do:

We are looking at adding possibly 5 more workstations.  We would also like to address the network load problem until that happens.  As ubuntu is very light on hardware requirements do we need to explore other options such as primary/secondary domain controllers, hardware level RAID to ensure sufficient network and application speed for the clients that are running intensive bandwidth and disk access software from the server?

Thank you!

---

### Post by rubylaser on 2011-04-13
Here's a couple quick questions.  What is your network infrastructure? (i.e. 10/100,10/100/1000, wireless).  What is your average throughput to the server in an average day?  

A RAID array would not be a bad idea just for the sake of redundancy, but will also benefit performance as well.  Bonded NICs would also be a good idea.

Have you performed any benchmarking to determine what is actually the bottleneck?  Look at iostat, view system resources with utilization on the server, view the network interface throughput, and test other transfer protocols to compare speed (try NFS at least).

---

### Post by earthpigg on 2011-04-13
Google is telling me that your NetVista is, at most, a P4 with 1.5gb of RAM. Is that correct?

Do you know what the current bottleneck is? It could be that the RAM is used up and heavy swap usage is in place, or it could be speed of the filesystem (fragmentation *can* be a concern even on linux, in extreme situations), etc.

I'd start by poking away at the server *while it is under heavy* load to find out why.

Ideally, you would be posting on ubuntuforums *while* the server is struggling under heavy load *and* while you are connected to it via ssh or similar.

---

### Post by dave37 on 2011-04-13
It is a 10/100/1000 adaptec card in the IBM netvista server, I am not using the onboard card, and yes, it is maxed out with 1.5gb ram and a p4.

I have not figured out the bottleneck as it occurs when I am at my day job (it is my wife's office) and of course all I get is vague "the network was slow at 1:30 today" without any idea what client pc's may have been doing, or if it was lan based or wan based activities they were doing when complaining of slow downs.  If you have any suggestions for net diagnostics that would allow me to do some sort of recording (I know that's really wishing!) or can point me to some good resources as they are working weekends for the next few weeks and I may have to opportunity to be logged in to the server when it occurs.

Average throughput, by looking at the nightly rsync logs for changed data, is about 200 mb to 1 gb.

Thanks much!

---

### Post by SeijiSensei on 2011-04-13
One guess is the hourly rsync process.  Performance is going to decline while the server and network are moving data around. 

I don't know what other tasks the HP server provides other than backup.  If that's its major task, consider adding network cards to both servers and using them to create a dedicated secondary network connection between the servers.  That will take the bandwidth demands during syncs off the main network.

Still the problem might have more to do with disk performance than network bandwidth.  What if you reduced the frequency of syncs, or staggered them throughout the day so they don't coincide with heavy workstation traffic?  Personally I think hourly syncs aren't worth it unless you really fear that the drives in the main server are going to go south sometime soon.  When was the last time you needed to restore the main server from backups?  Was having hourly backups important in this case?  I could see running backups at maybe 11am, 3pm and 7 pm. 

My experience from my clients' sites is that traffic is highest between 11am and 2pm if you let your staff access high-bandwidth sites like YouTube.  Pandora and other streaming services can also hog bandwidth that should be dedicated to actual business needs.  Do you have strict policies about what people can do with their workstations, and when they can do it?

I've installed Squid as a transparent proxy in clients' organizations to be able to manage web traffic.  You can write rules that automatically block, say, YouTube between 9 and noon and 2pm to 5pm.  With reporting software like [SARG]("http://sarg.sourceforge.net/sarg.php"), you can see which client IP addresses are the biggest web users. You might discover that only a handful of staff are using up most of the bandwidth visiting non-work-related sites.

You haven't told us about your router.  If your main router is a Linux box, consider installing something like [ntop]("http://www.ntop.org/overview.html") to analyze traffic and bottlenecks.  This would be the place to put that Squid proxy as well.

---

