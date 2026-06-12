---
title: "Question about website setup"
date: 2012-08-30
forum: General Help
---

### Post by Almeida1 on 2012-08-30
Hi,

I work between office and home on the same laptop. I'm a web developer and have got LAMP setup on my laptop. However, I am currently working locally and want to work on the network instead so that other colleagues can also work on the same website without having to have a separate one installed locally on their machine. 

We currently have a Ubuntu Virtual machine in the office which I'm considering putting the site on and mounting the drive to my laptop. I'm just wondering will this work? I'm pretty sure it will in the office, however what shall I do when I'm working from home and don't have access to the office network? Will I be able to still access the mount from home if my IP (from home) is allowed?

I'm just looking for some general ideas/help if possible?

Thanks

---

### Post by SlugSlug on 2012-08-30
if you install ssh server on work ubuntu and open up port 22 on work router to point to ubuntu machine's ip

then just mount a ssh share (via places in Nautilus) on lappy

---

### Post by greenpeace on 2012-08-30
If you have lots of people working on the same project, it would be worth considering using a collaboration tool like subversion or git, and having a central repository for the code.

Then you can just create a simple deployment script which takes the latest version from the repository and deploys it to the server.

Subversion is pretty simple to set up, and there is good support for IDEs on both windows and linux.  Also it gives good feedback on who has made a change... which can be very useful!

---

### Post by Almeida1 on 2012-08-30
> **SlugSlug said:**
> if you install ssh server on work ubuntu and open up port 22 on work router to point to ubuntu machine's ip

then just mount a ssh share (via places in Nautilus) on lappy

I've got a static IP on my laptop for when I'm in work so that I can connect to the office network, is it possible to have another static IP when I'm at home to point the work router to? What's the difference between ssh and nfs? I've got nfs setup at the moment for when I'm in the office so I can access the Ubuntu VM but assume I can't access this from home can I because I'm not on the same network?

---

### Post by Almeida1 on 2012-08-30
> **greenpeace said:**
> If you have lots of people working on the same project, it would be worth considering using a collaboration tool like subversion or git, and having a central repository for the code.

Then you can just create a simple deployment script which takes the latest version from the repository and deploys it to the server.

Subversion is pretty simple to set up, and there is good support for IDEs on both windows and linux.  Also it gives good feedback on who has made a change... which can be very useful!

Thanks for the tip. I'm currently using SVN already, however I need to be working on the server so I can communicate with 3rd partys which are built in the office and only allow communication from the office network. Hope that makes sense?

---

### Post by Almeida1 on 2012-08-30
I'll try and be a bit more clear, I was in a rush when I submitted the first post sorry.

I want to setup a LAMP stack which will contain a couple of websites and allow all colleagues to read/write to the website files either from in the office or from home. The websites need to communicate with 3rd party systems which are built in house and only allow access to anything within the office network.

I currently have a laptop with LAMP installed containing the websites which I use SVN to keep in sync with the other colleagues. However, this means we all have our own database and when at home we can't communicate with the 3rd party system. 

We have got a Windows server in the office which has got a Virtual Machine with Ubuntu and LAMP installed. Therefore, I have mounted this to my laptop and can run the website as expected. However, again this means we would need our own database (unless we can somehow access the database on the server?) Also, what happens when I go home? I won't be able to access the mount will I? 

Hope that clears things up a little.

Thanks

---

### Post by greenpeace on 2012-08-30
> **Almeida1 said:**
> However, again this means we would need our own database (unless we can somehow access the database on the server?)
What do you need to do from the database while you're coding?  

Could you take a weekly snapshot and distribute this as a "test" database to your developers?  Or just have a representative DB which has representative, but not live data so you can see how the site works as you develop it.

> **Almeida1 said:**
> Also, what happens when I go home? I won't be able to access the mount will I?
I would be tempted to have a dedicated ubuntu server set up to run your websites and the PHP stack as well as the SVN repo accessible over SSH - thereby allowing you all access from home.

Did I get understand you well enough?

---

### Post by dragonfly41 on 2012-08-30
Have you looked into Zend PHPCloud? 

[http://www.phpcloud.com/](http://www.phpcloud.com/)

[http://www.eschrade.com/page/setting-up-a-connection-to-the-zend-developer-cloud-on-linux/](http://www.eschrade.com/page/setting-up-a-connection-to-the-zend-developer-cloud-on-linux/)

---

### Post by Almeida1 on 2012-08-30
> **greenpeace said:**
> What do you need to do from the database while you're coding?  

Could you take a weekly snapshot and distribute this as a "test" database to your developers?  Or just have a representative DB which has representative, but not live data so you can see how the site works as you develop it.


I would be tempted to have a dedicated ubuntu server set up to run your websites and the PHP stack as well as the SVN repo accessible over SSH - thereby allowing you all access from home.

Did I get understand you well enough?

The database isn't too much of an issue to be honest because it won't be changing much at all, so if there are any changes I could simply ask them to inform the the other colleagues to also update theirs. 

Having a dedicated ubuntu server is something I've thought about, however would I have to have one in house or could I use something like rackspace even for development? Any other hosting services you recommend please let me know.

Thanks

---

### Post by Almeida1 on 2012-08-30
> **dragonfly41 said:**
> Have you looked into Zend PHPCloud? 

[http://www.phpcloud.com/](http://www.phpcloud.com/)

[http://www.eschrade.com/page/setting-up-a-connection-to-the-zend-developer-cloud-on-linux/](http://www.eschrade.com/page/setting-up-a-connection-to-the-zend-developer-cloud-on-linux/)

I've never heard of it to be honest, I'll certainly have a look. Does it do something similar to what I require?

---

### Post by dragonfly41 on 2012-08-30
Read from Zend site  ..

> ** 	Collaborate**

   	Zend Developer Cloud puts a major emphasis on enabling more effective  collaboration. Using a cloud-based environment for developing your apps  means you can easily share your code with co-workers, friends and users.   Zend Developer Cloud also enables you to take snapshots of your  application stack and have a team member join the project from exactly  the same place you are at.   And, Zend Developer Cloud is integrated  with Git to help you manage your source files, so you can easily  collaborate with your team members at the source code level.




---

