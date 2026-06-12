---
title: "Adito"
date: 2010-07-25
forum: General Help
---

### Post by iamgeniusrnti on 2010-07-25
Folks,

Working with Amahi server and the VPN app.  WHenever I want to activate a VPN tunnel thru ssl, the VPN server starts up "Adito" agent.  Normally in Windows, the agent pops up with a browser and basically lets you surf inside the VPN.

But when I use my Ubuntu, it says it's starting teh agent and then it just sits there and stalls out with failed to sync.

I checked the logs and this is all I got:

p kernel: [29491.039030] type=1503 audit(1280097273.298:147): operation="file_mmap" pid=8323 parent=8320 profile="/usr/lib/firefox-3.6.7/firefox-*bin//firefox_java" requested_mask="mr::" denied_mask="m::" fsuid=1000 ouid=1000 name="/home/genius/.adito/applications/adito-agent/agent.jar"
Jul 25 18:34:33 k-laptop kernel: [29491.059263] type=1503 audit(1280097273.318:148): operation="file_mmap" pid=8323 parent=8320 profile="/usr/lib/firefox-3.6.7/firefox-*bin//firefox_java" requested_mask="mr::" denied_mask="m::" fsuid=1000 ouid=1000 name="/home/genius/.adito/applications/adito-agent/maverick-ssl.jar"
Jul 25 18:34:33 k-laptop kernel: [29491.060507] type=1503 audit(1280097273.318:149): operation="file_mmap" pid=8323 parent=8320 profile="/usr/lib/firefox-3.6.7/firefox-*bin//firefox_java" requested_mask="mr::" denied_mask="m::" fsuid=1000 ouid=1000 name="/home/genius/.adito/applications/adito-agent/ui.jar"
Jul 25 18:34:33 k-laptop kernel: [29491.064901] type=1503 audit(1280097273.322:150): operation="file_mmap" pid=8323 parent=8320 profile="/usr/lib/firefox-3.6.7/firefox-*bin//firefox_java" requested_mask="mr::" denied_mask="m::" fsuid=1000 ouid=1000 name="/home/genius/.adito/applications/adito-agent/agent-swt.jar"
Jul 25 18:34:33 k-laptop kernel: [29491.067682] type=1503 audit(1280097273.326:151): operation="file_mmap" pid=8323 parent=8320 profile="/usr/lib/firefox-3.6.7/firefox-*bin//firefox_java" requested_mask="mr::" denied_mask="m::" fsuid=1000 ouid=1000 name="/home/genius/.adito/applications/adito-agent/maverick-util.jar"
Jul 25 18:34:33 k-laptop kernel: [29491.068795] type=1503 audit(1280097273.326:152): operation="file_mmap" pid=8323 parent=8320 profile="/usr/lib/firefox-3.6.7/firefox-*bin//firefox_java" requested_mask="mr::" denied_mask="m::" fsuid=1000 ouid=1000 name="/home/genius/.adito/applications/adito-agent/swt-linux.jar"
Jul 25 18:34:33 k-laptop kernel: [29491.069991] type=1503 audit(1280097273.330:153): operation="file_mmap" pid=8323 parent=8320 profile="/usr/lib/firefox-3.6.7/firefox-*bin//firefox_java" requested_mask="mr::" denied_mask="m::" fsuid=1000 ouid=1000 name="/home/genius/.adito/applications/adito-agent/agent-swt-en.jar"
Jul 25 18:34:33 k-laptop kernel: [29491.071146] type=1503 audit(1280097273.330:154): operation="file_mmap" pid=8323 parent=8320 profile="/usr/lib/firefox-3.6.7/firefox-*bin//firefox_java" requested_mask="mr::" denied_mask="m::" fsuid=1000 ouid=1000 name="/home/genius/.adito/applications/adito-agent/maverick-crypto.jar"
Jul 25 18:34:33 k-laptop kernel: [29491.072314] type=1503 audit(1280097273.330:155): operation="file_mmap" pid=8323 parent=8320 profile="/usr/lib/firefox-3.6.7/firefox-*bin//firefox_java" requested_mask="mr::" denied_mask="m::" fsuid=1000 ouid=1000 name="/home/genius/.adito/applications/adito-agent/log4j-java1.1.jar"
Jul 25 18:34:33 k-laptop kernel: [29491.073589] type=1503 audit(1280097273.334:156): operation="file_mmap" pid=8323 parent=8320 profile="/usr/lib/firefox-3.6.7/firefox-*bin//firefox_java" requested_mask="mr::" denied_mask="m::" fsuid=1000 ouid=1000 name="/home/genius/.adito/applications/adito-agent/agent-en.jar"


What am I missing??? Help?

---

### Post by iamgeniusrnti on 2010-07-26
OK so I discected the log and did some googling for a while and discovered that if I disable Apparmor, the java script works.
 
So... apparmor... is there a line I can put in the /etc/apparmor profile to loosen up leash, or do I just disable it when I need to do a vpn?

---

### Post by iamgeniusrnti on 2010-07-27
Bump?

---

