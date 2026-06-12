---
title: "Ubuntu 10.10 fail?"
date: 2010-10-27
forum: General Help
---

### Post by Ana.Gene on 2010-10-27
Hello,

[COLOR=#000000][FONT=Times New Roman][FONT=arial][B]I am running Ubuntu 10.10  server edition (64-bit)

[/B][/FONT][/FONT][/COLOR] I recently upgraded to Ubuntu 10.10 and since then I have had a couple of problems. The first and the most major one is that it does not look like its supposed to. I am relatively new to Linux so any help would be appreciated:

Major issues:
The top and bottom bars are supposed to be black instead they are a solid ugly Grey. I restarted a couple of times and once it went back to normal (black) but then it crashed and since then it has been resolutely grey. I think this is a symptom of a greater ill. I can work with it, but my jobs take hours to run and I worry the system will crash suddenly.

Minor issues:
EPIC Perl no longer works with Eclipse. I had it going happily and successfully in 10.04 and now going through the same steps it seems to be installed but doesn't show up. I think this may also be a symptom of a great ill. I did the whole uninstall/re-install EPIC as well as uninstall/re-install Ecplise to no avail

Things I did that may have broken it:
Finally, everything seemed to start messing up when I did one thing (which admittedly I am not sure what is does 100%). We run this software for Genetic Analysis and it has known issues to Ubuntu 10.04 and above. It was some glibc issue. A lot of people had problems with it, but there was a work around on the forums and this was it:

[COLOR=#000000][FONT=Times New Roman][LEFT][FONT=arial]sudo apt-get install nscd
# open /etc/nscd.conf with your $EDITOR
# find following line:
# enable-cache hosts no
# change "no" to "yes"
# save & exit the editor
sudo service nscd restart

Any help would be appreciated. I don't want to run further analysis and have it fail.



[/FONT][/LEFT]
[/FONT][/COLOR]

---

