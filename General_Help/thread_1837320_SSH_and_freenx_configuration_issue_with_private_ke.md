---
title: "SSH and freenx configuration issue with private keys"
date: 2011-09-01
forum: General Help
---

### Post by spectre85 on 2011-09-01
Hello, first off I'm not that good in linux so bare with me please. 

My issue, I recently set up SSH on my home machine and can tunnel in from work no problem.  I also have freenx set up and can tunnel in from work no problem.  I've also wanted to use custom keys with a public/private key.  SO I set that up and finally got it working.  

Now my problem comes in I am not able to connect with nomachine without a password and the whole point of using custom keys is to get rid of the password so I can't be brute forced.  unfortunatly nomachine doesn't work without a password.....so is there any way to fix this.  both nomachine and ssh have working public/private keys but as soon as I turn off the password field in sshd_config nomachine can't connect, when I turn it back on I am able to connect using the default keys (which is what I dont want).  

Should I just use somethign else like VNC or what would be best here?  Thx guys

my machine at work is a windows 7 box.

---

