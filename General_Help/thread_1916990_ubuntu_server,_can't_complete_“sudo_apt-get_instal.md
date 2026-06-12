---
title: "ubuntu server, can't complete “sudo apt-get install ubuntu-desktop”"
date: 2012-01-29
forum: General Help
---

### Post by moaaz300 on 2012-01-29
[CENTER]I'va installed ubuntu server 10.41 in Vm ware, and I would like to install the desktop
[/CENTER]
 but each time i try to do the command sudo apt-get install ubuntu-desktop
this error shows up:


  Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libproxy/](http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libproxy/) libproxy0-o.3.1-ubuntu1-amd64.deb 403 Forbidden [Ip:91.189.92.179 80]  E:ubable to fetch some archives,maybe run apt-get update or try with fix --missing?   

I tried fix missing command but didn't work for the same reason. I tried to cahnge the proxy like this:

  
[LIST=1]
[*]changed the proxy in my host computer. (ultra serf)
[*]changed the proxy settings in my VM to Bridged And Riplicate physical network Connection
 state.
[*]run the command:

  export http-proxy
http-proxy=http://127.0.0.1:80 

same problem, so mybe i should change the proxy settings in ubuntu but I don't know how


 By the way the missing file that is refusing to be downlaoded is 38.1KB and all other files are perfectly downloaded
so maybe i can just download it in the host(windows xp) and move to ubuntu
 but i don't know where is the directory for the downloaded package OR where can i add this file, can any one help me?
[/LIST]

---

### Post by jerrrys on 2012-01-30
Your command looks a little off.

[https://help.ubuntu.com/community/AptGet/Howto#Temporary_proxy_session](https://help.ubuntu.com/community/AptGet/Howto#Temporary_proxy_session)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+proxy&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+proxy&sa=Search&cof=FORID:9)

---

