---
title: "Aptitude always point to internal IP"
date: 2012-01-06
forum: General Help
---

### Post by s4510488 on 2012-01-06
I am not sure why this happens since a few days ago I could install the package using Aptitude without
any problem. But today when issuing a command like the following causes an error.
Notice that it points to 192.168.10.101 which is an internal IP address.

[I]woraphol@woraphol-A8J:~$ sudo apt-get update
Err [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                                                                                                             
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease                                                                                                                
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates InRelease                                                                                             
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security InRelease                                                                                            
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release.gpg                                                                                                   
  Unable to connect to** 192.168.10.101:3128:**
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release.gpg                                           
  Unable to connect to 192.168.10.101:3128:
Err [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                                                
  Unable to connect to 192.168.10.101:3128:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security Release.gpg                                          
  Unable to connect to 192.168.10.101:3128:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                                      
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                                      
  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg    
  Unable to connect to 192.168.10.101:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg
  Unable to connect to 192.168.10.101:3128:
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty/InRelease](http://archive.ubuntu.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-security/InRelease](http://archive.ubuntu.com/ubuntu/dists/natty-security/InRelease)  

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/natty/InRelease](http://archive.canonical.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/InRelease](http://extras.ubuntu.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/natty/InRelease](http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/natty/Release.gpg](http://archive.canonical.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to 192.168.10.101:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to 192.168.10.101:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg)  Unable to connect to 192.168.10.101:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/natty-security/Release.gpg)  Unable to connect to 192.168.10.101:3128:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to 192.168.10.101:3128:

W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/natty/Release.gpg](http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/natty/Release.gpg)  Unable to connect to 192.168.10.101:3128:

W: Some index files failed to download. They have been ignored, or old ones used instead.[/I]

I would like to know how to reset it back for Aptitude to point to the original repository.
Thank in advance.

---

### Post by spacecheck on 2012-01-06
Did you use the computer somewhere else and have perhaps set a proxy for that location?

Good luck!

---

### Post by dcstar on 2012-01-07
> **s4510488 said:**
> I am not sure why this happens since a few days ago I could install the package using Aptitude without
any problem. But today when issuing a command like the following causes an error.
Notice that it points to 192.168.10.101 which is an internal IP address.
............
W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/natty/Release.gpg](http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/natty/Release.gpg)  Unable to connect to **192.168.10.101:3128**:

W: Some index files failed to download. They have been ignored, or old ones used instead.[/I]

I would like to know how to reset it back for Aptitude to point to the original repository.
Thank in advance.

That is the IP address and Port of a Proxy Server. If you do not use a Proxy Server then you will have to make the necessary changes to Synaptic and the System wide Proxy settings.

---

