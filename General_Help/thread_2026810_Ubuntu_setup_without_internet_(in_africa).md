---
title: "Ubuntu setup without internet (in africa)"
date: 2012-07-15
forum: General Help
---

### Post by stoopkitty on 2012-07-15
I am going to Uganda soon for a service trip and someone in the village I am going to asked me about bringing software such as educational games and encyclopedias for computers. I immediately thought of installing ubuntu on all the computers, because it is easy to install, open source, and works on a wide range of systems. 

However, they have sparse electricity in the village, and I can't imagine that they would have internet access. How do you think that I should go about doing this? Should I just bring the standard 32bit Ubuntu 12.04 on a disc and install it, then load up a flash drive or another disc with all the packages for the programs I want to bring? Is there another version of ubuntu that would be better, or do I need to bring multiple versions?

I've used Ubuntu desktop a little bit over the past few years and I put Ubuntu server on the personal server at my house, but I thought it would be best to ask experienced users to see if they have any additional thoughts on how I should go about this.

Thanks,
Josh

---

### Post by GreatDanton on 2012-07-15
Well, this is not really the solution for your problem, but maybe you should try Debian, which has dvd option, so you download the OS with a bunch of software.

---

### Post by elliotn on 2012-07-16
install all the required software on your PC and remaster it into an ISO then go install in Uganda

---

### Post by stoopkitty on 2012-07-16
> **elliotn said:**
> install all the required software on your PC and remaster it into an ISO then go install in Uganda

remaster, that was all i needed. thanks. [this]("https://help.ubuntu.com/community/LiveCDCustomization") is the page I need, correct?

---

### Post by Cheesemill on 2012-07-16
> **stoopkitty said:**
> remaster, that was all i needed. thanks. [this]("https://help.ubuntu.com/community/LiveCDCustomization") is the page I need, correct?
Use Remastersys instead, it's much easier.
[http://www.geekconnection.org/remastersys/index.html](http://www.geekconnection.org/remastersys/index.html)

---

### Post by Lars Noodén on 2012-07-16
Another way, which compliments the method above, would be to use [apt-cacher](https://help.ubuntu.com/community/Apt-Cacher-Server) to build a portable repository.  You could build the basic set up with remastersys and have the extras in apt-cacher.  It's very easy to set up and use.

---

### Post by techvish81 on 2012-07-16
try it before you go.  :)

---

