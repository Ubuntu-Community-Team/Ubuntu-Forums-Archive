---
title: "Home made server set up?"
date: 2010-12-15
forum: General Help
---

### Post by codydbgt on 2010-12-15
So this is what i want to do i want to be able to run many things like networked dvr system, srcds server, file hosting/web related prorgrams, and a home network like they have set up a schools only better....not as bugggy. I have a pc with ubuntu 10.10 on it and 2 srcds consoles running. So if i want to expand and exparenment on thoes other things what kind of pc setup am i looking at. For the mony of course. Im not shure if cloud computing would get me there but when i get some extra cash i can add pcs to it. Or can i do half of them things with a real good pc.

I have experence in curicuts and stuff but have never messed around with homade pc building im doing reaserch but i still have know idea how do do the home network or the cloud computing thing. Yes i have general knowlage i  routers swichs and well pcs and ther internals. i know the idea of a buss and buffers and cashes and regesters and memory. so you dont need to teach me every thing. what would you do is what im asking? And do i need to venture into other linux os's and what kind of hardwear should i pick out....mother boards brands and models, cpu's, and memory. well i think i understand memory very well and procesers some what well so give me any thing reaserch links guides and or your help. I need a plan on what to buy/save up for and in the meen time i can learn the softwear that i will be using. 

Thanks if any one took the time to read this. i may have lost you some where sorry if i did. If i did ask questions and i didnt realy know where this post would have gone. :O sorry if i did put this in the wrong spot dont deleat it.

---

### Post by codydbgt on 2010-12-15
Did i post in the wrong forms?

---

### Post by arvevans on 2010-12-15
You may have to wait a while for results.  Some people have lives outside of Linux and jobs that keep them away from their computer for 8 or so hours per day.  Re-posting and bumping too often may decrease the chances of getting responsible answers.

Now, having said that, I gather from your post that you want to do a number of things, with one of them being to set up your own home server.  There are a number of excellent server packages.  At the risk of starting a big server argument I will state that the usual Linux system web server is Apache, but there are many others, each with it's own pro's and con's.

I use a small web server package called Cherokee.  It is tight, fast, and easily understood.  Go [here]("http://www.cherokee-project.com/") to see what it is all about.

I set up my Cherokee web server on an older PC (1.2 GHz CPU, 500 MB RAM, 160 GB HD, etc.) and linked my desktop to it's file system with NFS (Network File Service) so that it's web file area looks like a part of my regular desktop computer.  This lets me run various web page editors on my higher-performance desktop computer and seamlessly edit web page content where it resides on the web server.

Most web server programs will let you run interactive programs via the server access.  Security is sometimes a problem but is manageable with some research toward developing your knowledge base on firewalls and such.  To run interactive applications via a web server the application is usually called from an entry in [web_server_location]/cgi-bin.  This is where you put executables that can be called by clicking on a web served URL.

I run a local tertiary DNS server that links to primary and secondary DNS servers in the usual manner.  That function resides in configuration of my LAN (Local Area Network) Router/Hub/Wi-Fi host.  If you run DNS functions on a Linux system and expose that system outside your firewall, it is possible to set up a pseudo-private network based on your own DNS references and offer subscription access to that server.  You could also do this with static IP's but the DNS thing is more elegant and more fun.

Break down your list of things that you want to do, then do individual Google searches for each of them by name.  Read several of the resulting tutorials that relate to what you want to do.  This is the way to learn about various applications and configuration required to make them work.

If you do a Google search for "Source Dedicated Server" you will find that there are now ways to host this directly on a Linux system, and how do do that.  Not being a gamer, I cannot help you much beyond just pointing at some of the available on-line information.

If you really get stuck on some point that you absolutely cannot find the answer for, then come back to this forum and ask specific questions related to the problem.  There is a massive amount of knowledge represented by those who usually lurk here, but you should not waste their time with very generalized questions when the answer can be found on the Internet with a few searches and some reading.

---

### Post by e24ohm on 2010-12-15
I would also recommend to download a copy of Ubuntu Server Edition. Getting the experience form the CLI is really good, and should start you thinking outside the GUI box.

Good Luck!!!

---

### Post by codydbgt on 2010-12-16
So since i must of missed led you.im realy need to know more about what kind of os and network set up and hardwear for each pc if i do a cluster or cloud. I want to do many more projects than this in the future but i want to know what kind of set up is the moste expandable and can have multiple projects and still have importan thjngs run....like my srcds. Basickly i am an expert on srcds and need to know if i can make a cloud or cluster to so i can run many srcds on one system iv done some reaserch on cloud computing and clustering and it many depends on the prorgram. But is it possable to share memory over the network.or can i just have a set up where you load a prorgram on a master server but it actualy will open it on a node that is up to the job what ever it is so open srcds visably opens on the master node and is realy running on a nother node?

---

