---
title: "Problem Installing ANOTHER program..."
date: 2006-06-14
forum: General Help
---

### Post by t.z0n3 on 2006-06-14
I was trying to install Audacity so that I can record audio for my podcast I plan to get up soon, but it won't work. I previously posted in Gaming about a problem installing Enemy Territory, but that's fine now. I tried to use the same methods to install this, but it didn't work. Here's what I get:

Audacity requires the following package: libwxgtk2.4-1

So I installed that, and then I make my way back to the audacity file (.deb type) and double click it again: it insists that the required package has NOT been installed. I reinstall it to make sure, same message. I also tried to install it via terminal, tried to make it an executable, and tried to use apt-get. 

UGH. 

Please help?:confused:

---

### Post by mjm115 on 2006-06-14
Have you tried installing from the repository or from a downloaded .deb file?  It's in the universe repository.  Do you have that enabled?  What does the exact error message say?

---

### Post by PriceChild on 2006-06-14
try using a "-i" parameter :S.... maybe 
 
e.g. "sudo dpkg -i <<name>>.deb
 
If you've got the internet on this pc and the universe enabled, why not just "sudo apt-get install audacity" ?

---

### Post by t.z0n3 on 2006-06-14
Thanks again for your help. Yeah, it was the universe repositories, I didn't have those enabled.

Though, for the record, I DID try to apt-get everything, and that puked a few times. Probably because of the repostitories... :-& 

Sorry about my uber cluelessness, and thanks to you guys who put up with me. I'll get good at this eventually... :D

---

