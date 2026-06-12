---
title: "no output load in poweware"
date: 2012-04-18
forum: General Help
---

### Post by associates on 2012-04-18
Hi,

I was trying to get UPS Powerware 5110 to work with my machine running on Ubuntu Server 10.04. I followed the instruction described at ubuntuforums.org/showthread.php?t=1443562. Everything seemed to work fine at the start. Then I went to check to see if the powerware UPS is actually working by running the command 
```

sudo upsc Powerware5110
```

I got the following result:
ambient.temperature.high: 1
battery.charge.low: 22
battery.voltage:  26.9
device.mfr: Eaton
device.model: POWERWARE UPS    1000i
device.serial: 
device.type: ups
driver.name: bcmxcp_usb
driver.parameter.pollinterval: 2
driver.parameter.port: auto
driver.version: 2.4.3
driver.version.internal: 0.23
input.frequency:  50.1
input.frequency.high: 55
input.frequency.low: 45
input.frequency.nominal: 50
input.transfer.boost.high: 216
input.transfer.high: 280
input.transfer.low: 186
input.transfer.trim.low: 260
input.voltage: 244
input.voltage.nominal: 240
output.current:   0.0
output.current.nominal:   2.5
output.frequency:  50.1
output.phases: 1
output.voltage: 244
output.voltage.nominal: 240
ups.beeper.status: enabled
ups.firmware: Cont:00.50 Inve:01.50
ups.load:   0.0
ups.mfr: Eaton
ups.model: POWERWARE UPS    1000i
ups.power.nominal: 1000
ups.serial: 
ups.status: OL

My concern is why it shows the ups load is 0.0 when it has been connected to the machine. There must be some loads, must not there?

Any help would be greatly appreciated.

Thank you

---

### Post by HiImTye on 2012-04-18
Im pretty sure that it should only have a load on the UPS when it is running off the UPS battery, otherwise it should have a 0 load if you are using AC

---

### Post by associates on 2012-04-18
Thank you for your reply.

I did a test by unplugging the power cord for powerware UPS from the power socket to make it look like there is a power outage. The server (which is connected to the UPS) was still running. But after waiting for a minute, I did not see any popup message with a warning indicator that the shutdown countdown is underway or something on the server. I got a feeling that the server would only shut down after the UPS runs out of power. If this is the case, this would cause an abrupt shutdown which is no good to the server. However, it could also be the case where the server gets proper shutdown just before the UPS runs out of battery. I have not yet experimented this.

I wonder if we could set a timer as to how long for we want the server to run way before the UPS runs out of power in Ubuntu.

Thank you very much

---

### Post by dcstar on 2012-04-19
Do not totally change the subject of the thread.

Start a new thread with your separate issue.

---

