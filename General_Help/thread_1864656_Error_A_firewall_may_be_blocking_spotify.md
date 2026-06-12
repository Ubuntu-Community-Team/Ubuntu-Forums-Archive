---
title: "Error: A firewall may be blocking spotify?"
date: 2011-10-19
forum: General Help
---

### Post by bmwman on 2011-10-19
Hi all,
I installed the latest Spotify from a .DEB that i downloaded from here [http://repository.spotify.com/pool/non-free/s/spotify/]("http://repository.spotify.com/pool/non-free/s/spotify/"). Install went through fine with the Ubuntu Software Center and the program starts fine. The issue is when i try to sign in, it throws this error : "A firewall may be blocking Spotify. Please update your firewall to allow Spotify". I am running 11.10 and the firewall is turned off by default. Spotify works fine if i boot into Windows (this is my work PC) so i doubt the ports are blocked at work, unless the Linux version uses a different port. Any ideas what the problem might be? Thanks

---

### Post by SparTacux on 2011-10-19
Try observing the network traffic using netstat -ntuc

It might lead you to the source of any network problems.

---

### Post by khanley52 on 2011-10-21
I'm having this same issue.  I miss my Spotify. :(

---

### Post by sheazar on 2011-10-24
I had the same issue. At least in my case it was because I needed to upgrade the client. The upgrade to 11.10 had disabled the spotify repo so I didn't get any updates anymore.

Uncomment deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free in /etc/apt/sources.list

run sudo apt-get update && sudo apt-get upgrade

That solved it for me at least...

---

### Post by khanley52 on 2011-10-25
The way I fixed it was to upgrade my Spotify account to premium.  Wish I had tried your way first. :P

---

