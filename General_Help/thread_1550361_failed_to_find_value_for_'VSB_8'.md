---
title: "failed to find value for 'VSB_8'"
date: 2010-08-11
forum: General Help
---

### Post by Thomas Garman on 2010-08-11
I am using ME-TV and w-scan to generate a channels.conf file.  ME-TV spits out "failed to find value for 'VSB_8'"

I am using the PINNACLE 801SE USB stick as a tvtuner and I have the correct dvb driver installed and I am running LUCID 10.04.  Please do not respond by saying I should use some other TV viewers because I have tried them all, none will capture the stream and play tv even though the device is recognized and my channels.conf file from w_scan looks like this:

WLS-DT:177000000:VSB_8:49:52:1
Livwell:177000000:VSB_8:65:68:2
WLS-SD:177000000:VSB_8:81:84:3
WGN-DT:503000000:VSB_8:49:52:3
service_id 4:503000000:VSB_8:65:68:4
WYCC HD:515000000:VSB_8:49:52:1
WYCC SD:515000000:VSB_8:65:68:2
MHZ:515000000:VSB_8:81:84:3
WCIU-DT Chicago:551000000:VSB_8:49:52:3
WWME-CA Chicago:551000000:VSB_8:65:68:4
WMEU-CA Chicago:551000000:VSB_8:81:84:5
THIS Chicago:551000000:VSB_8:97:100:6
Chicago Ethnic Television:551000000:VSB_8:129:132:8
WWME-CA Chicago:551000000:VSB_8:65:68:9
WMEU-CA Chicago:551000000:VSB_8:81:84:16
NBC5   :563000000:VSB_8:81:84:5
NBC5-WX:563000000:VSB_8:97:100:6
NBC5-US:563000000:VSB_8:113:116:7
WFLD   :575000000:VSB_8:49:52:3
WJYS Digital - Your station for inspiration.:605000000:VSB_8:49:51:1
My Christian TV:605000000:VSB_8:65:67:2
WJYS2:605000000:VSB_8:97:99:4
Univision Chicago:617000000:VSB_8:49:52:1
WWME-CA Chicago:623000000:VSB_8:49:52:3
WCPX ION Life:647000000:VSB_8:81:84:5
WCPX qubo:647000000:VSB_8:65:68:4
WCPX Digital Television:647000000:VSB_8:49:52:3
WLS-DT:653000000:VSB_8:49:52:1
Livwell:653000000:VSB_8:65:68:2
WLS-SD:653000000:VSB_8:81:84:3
WSNS HD:659000000:VSB_8:49:52:3
Inmigrante TV
WSNS-TV
454 N. Columbus Drive
Chicago, IL 60611
312-836-5555:659000000:VSB_8:65:68:4
WTTW-HD:671000000:VSB_8:49:52:3
WTTW-DT:671000000:VSB_8:65:68:4
WTTW-DT:671000000:VSB_8:81:84:5
WTTW-DT:671000000:VSB_8:97:100:6
WXFT-HD Telefutura Chicago:689000000:VSB_8:49:52:1
WXFT-SD Telefutura Chicago:689000000:VSB_8:65:68:2
WPWR-TV:695000000:VSB_8:49:52:3
WLS-DT:177000000:VSB_8:49:52:1
Livwell:177000000:VSB_8:65:68:2
WLS-SD:177000000:VSB_8:81:84:3
WGN-DT:503000000:VSB_8:49:52:3
service_id 4:503000000:VSB_8:65:68:4
WYCC HD:515000000:VSB_8:49:52:1
WYCC SD:515000000:VSB_8:65:68:2
MHZ:515000000:VSB_8:81:84:3
WCIU-DT Chicago:551000000:VSB_8:49:52:3
WWME-CA Chicago:551000000:VSB_8:65:68:4
WMEU-CA Chicago:551000000:VSB_8:81:84:5
THIS Chicago:551000000:VSB_8:97:100:6
Chicago Ethnic Television:551000000:VSB_8:129:132:8
WWME-CA Chicago:551000000:VSB_8:65:68:9
WMEU-CA Chicago:551000000:VSB_8:81:84:16
NBC5   :563000000:VSB_8:81:84:5
NBC5-WX:563000000:VSB_8:97:100:6
NBC5-US:563000000:VSB_8:113:116:7
WFLD   :575000000:VSB_8:49:52:3
WJYS Digital - Your station for inspiration.:605000000:VSB_8:49:51:1
My Christian TV:605000000:VSB_8:65:67:2
WJYS2:605000000:VSB_8:97:99:4
Univision Chicago:617000000:VSB_8:49:52:1

---

### Post by Thomas Garman on 2010-08-11
Anyone have any ideas?  Basically w-scan does not generate a channels.conf file that can be read by ME-TV.

---

### Post by Flokko on 2010-09-14
Hi there,

I'm facing te same problem at the moment. 

Changing the VSB_8 to 8VSB should solve it.

The strange thing is, that I've one channelscan from south california and the modulation info is correct. 8VSB

The other channels file from upper north in californai shows the wrong modulation VSB_8.

Can anybody explain why this is - as it is?

Cheers,
Flo

---

