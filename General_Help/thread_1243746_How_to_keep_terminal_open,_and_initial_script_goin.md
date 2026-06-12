---
title: "How to keep terminal open, and initial script going"
date: 2009-08-18
forum: General Help
---

### Post by redhotfire on 2009-08-18
> **]
#!/bin/bash

echo -n "Enter device to be used: "
read Device1


xterm -e airmon-ng stop $Device1
xterm -e airmon-ng start $Device1

echo -n "Any more? "
read Decision	
	if [ $Decision == 'yes' ] said:**
> ; then
xterm -e airodump-ng -c $channel -w $fileLocation --ivs $airDevice
	else 
xterm -e airodump-ng -c $channel -w $fileLocation $airDevice
fi
exit 1

I was wondering if someone could help me with a script I am making but having problems with. When I call airmon, airodump or etc, it opens into xterm but I need to close xterm in order for the initial script to keep going. What am I doing wrong, and how can I fix those problems or any other problems in the script.

Thanks,
red

---

### Post by Slim Odds on 2009-08-18
You need to put an & at the end of the xterm line

That makes it run in the background.

You might want to look at nohup

---

### Post by redhotfire on 2009-08-18
> **Slim Odds said:**
> You need to put an & at the end of the xterm line

That makes it run in the background.

You might want to look at nohup
That worked perfectly, thank you. I will only run this while logged on so I have no need for nohup, but it was a interesting read on wiki.

Thanks,
red

---

### Post by HiImTye on 2009-08-18
you can also ctrl+z and type 'bg' into the terminal if you forget the &

---

