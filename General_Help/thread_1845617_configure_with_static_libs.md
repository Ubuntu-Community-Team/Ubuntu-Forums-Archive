---
title: "configure with static libs"
date: 2011-09-17
forum: General Help
---

### Post by gosk on 2011-09-17
Hi,

I am developing an embedded device using arm platform and there I want to install a mad player in the target. for that I want to copile it in my host with static libraries. I already tried using
--enable-static --disable-shared
options in the configuration command. Although the command generates static libs, the executable program still requires shared libs when I try command "arm-linux-readelf -d /location/madplay " 

what should I do in order to build the program completely static ?

thank you.
                                                                                                                   [IMG]http://lqcdn.thequestionsnetwork.net/questions/images/icons/useragent/icon_linuxubuntu.gif[/IMG]          [IMG]http://lqcdn.thequestionsnetwork.net/questions/images/statusicon/forum_old.gif[/IMG]                          [[IMG]http://lqcdn.thequestionsnetwork.net/questions/images/buttons/reputation.gif[/IMG]]("http://www.linuxquestions.org/questions/reputation.php?p=4474452")                                                                                            [[IMG]http://lqcdn.thequestionsnetwork.net/questions/images/buttons/report.gif[/IMG]]("http://www.linuxquestions.org/questions/report.php?p=4474452")

---

