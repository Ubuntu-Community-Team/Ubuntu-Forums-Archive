---
title: "Anyone a FrostWire user?"
date: 2009-10-19
forum: General Help
---

### Post by iTheBadGuy on 2009-10-19
I was using frostwire happily in my last Ubuntu installation, i switched to Kubuntu, but then back to Ubuntu.. now i have all my programs back except for FrostWire, i can't seem to start it up after the installation is complete. I get this when i try to open it through terminal:

"sudo frostwire". or just "frostwire": ```
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_16]
Configuring environment...
Loading FrostWire:
CLASSPATH SET TO: :./jaudiotagger.jar:./onion-fec.jar:./forms.jar:./commons-codec-1.3.jar:./vorbisspi.jar:./FrostWire.jar:./icu4j.jar:./themes.jar:./jcraft.jar:./ProgressTabs.jar:./log4j.jar:./daap.jar:./gettext-commons.jar:./httpcore-nio-4.0-beta2.jar:./guice-1.0.jar:./looks.jar:./jogg.jar:./jdic.jar:./messages.jar:./mp3spi.jar:./jmdns.jar:./jflac.jar:./jorbis.jar:./tritonus.jar:./clink.jar:./commons-logging.jar:./httpclient-4.0-alpha3.jar:./aopalliance.jar:./lw-all.jar:./onion-common.jar:./jdic_stub.jar:./httpcore-niossl-4.0-alpha7.jar:./jl.jar:./httpcore-4.0-beta2.jar:./jython.jar:./junit.jar:./foxtrot.jar
Invalid or corrupt jarfile FrostWire.jar


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_16"
Java(TM) SE Runtime Environment (build 1.6.0_16-b01)
Java HotSpot(TM) Client VM (build 14.2-b01, mixed mode, sharing)

ithebadguy@iTheBadDesktop:~$ 
```I did ```
sudo apt-get remove frostwire
``` and reinstalled it, but it's still giving me the same error. Also, i did ```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
``` Terminal said this "sun-java6-jre is already the newest version."

I downloaded the .deb from the home page - [http://www.frostwire.com](http://www.frostwire.com). 

What am i doing wrong? -_-'

---

### Post by iTheBadGuy on 2009-10-19
Guys.. my post is echoing in here :(

---

### Post by MelDJ on 2009-10-19
try removing java and then install frostwire. let it install java with itself

---

### Post by iTheBadGuy on 2009-10-19
Ok, thanks. Command to remove java please?

Edit: ```
[SIZE=2][COLOR=#808000]sudo apt-get remove sun-java6-jre sun-java6-plugin sun-java6-fonts
```[/COLOR][/SIZE]

?..

---

### Post by MelDJ on 2009-10-19
sudo apt-get remove sun-java6-jre sun-java6-plugin sun-java6-fonts

---

### Post by iTheBadGuy on 2009-10-19
I removed Java, with that cmd. i then tried to install frostwire with the .deb file i downloaded from the home page. It continues to give me basically the same Error.. ```
ithebadguy@iTheBadDesktop:~$ frostwire
Error: Could not open jar file: FrostWire.jar
/usr/lib/frostwire/unpack200.py:10: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
jaudiotagger.jar=E26869F145A5CDCFF36C0E199336DE0C
onion-fec.jar=A81777A25CD126A82145CDEA9E90546F
forms.jar=BAF81035F5507958C7DA459591D9E51C
commons-codec-1.3.jar=198BBDF29A8EFD936629A08CF1AA47F0
vorbisspi.jar=5243091A899D4FDD3DF4658F1F35EC00
FrostWire.jar=926F079AA72CA615D654897C61462513
icu4j.jar=0BAA17E78B089CB05DC0B7D46C3332FB
themes.jar=869526C7C76015BA49E9C87C335666A8
jcraft.jar=B64B52EBB5FF8EB24921C24718E348AD
ProgressTabs.jar=5ED641ADC982C69036C5BD912043CB89
log4j.jar=ADEEC7CAA0C5B3EF7461DB841DD3468C
daap.jar=6580251125124101D643B770B0DE006D
gettext-commons.jar=9D0ADAE2891EA3EB2B993FBE44AEAA4F
httpcore-nio-4.0-beta2.jar=8993AAFEFBC65D60F86C049024FA0310
guice-1.0.jar=5ABC7FE2AD6FA03C32D1E066202FDD5F
looks.jar=2104D8A3855074A625C23F00598EEA7B
jogg.jar=D7158C6BE281C7CFB0CD465D3E38B578
jdic.jar=7EC4DCDE24979510DB429D01C17EB2DE
messages.jar=26699708FDDBCE2EE64DB2A9B92AA3DE
mp3spi.jar=3EEDE9F242CB5E41309F06E26D5C10AB
jmdns.jar=F61E94168AE87EC532C8D0EAC646C602
jflac.jar=9CB8B5FF827563223C0E2E1839B593AB
jorbis.jar=209490C77A48996D484BA28367EA922B
tritonus.jar=EC93636020CC420E8658627FA8F1F5EF
clink.jar=4785F0D3FF414851C0A50BFAC42EE209
commons-logging.jar=BD2F6D6660AEC075E19F49435F9A421E
httpclient-4.0-alpha3.jar=5477E63678A68361CA332D067D74A7D0
aopalliance.jar=531C1CCBF674C048960C6505FD70F927
lw-all.jar=22BE11E8E5EC1A315E2216BA9D1BB97D
onion-common.jar=98DF1F561DFDDC49E84AC23A15623322
jdic_stub.jar=FB56DFA7979F98AA769E4E8691ABDDC5
httpcore-niossl-4.0-alpha7.jar=AD0A68739C093802B4FB0909B80724B6
jl.jar=720D43596F1B6DBA2CAEC505B74FF007
httpcore-4.0-beta2.jar=BB05452D6A2524B272B50E5DA126ED60
jython.jar=4F1007C908363C9B8B6CCCBF895B82EC
junit.jar=1815E5900DAE3CD1153DFA0D5A7013DD
foxtrot.jar=453729BA2BA2C9CA5B5FDD387D80BB28
HOSTNAME IS iTheBadDesktop
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_16]
Configuring environment...
Loading FrostWire:
CLASSPATH SET TO: :./jaudiotagger.jar:./onion-fec.jar:./forms.jar:./commons-codec-1.3.jar:./vorbisspi.jar:./FrostWire.jar:./icu4j.jar:./themes.jar:./jcraft.jar:./ProgressTabs.jar:./log4j.jar:./daap.jar:./gettext-commons.jar:./httpcore-nio-4.0-beta2.jar:./guice-1.0.jar:./looks.jar:./jogg.jar:./jdic.jar:./messages.jar:./mp3spi.jar:./jmdns.jar:./jflac.jar:./jorbis.jar:./tritonus.jar:./clink.jar:./commons-logging.jar:./httpclient-4.0-alpha3.jar:./aopalliance.jar:./lw-all.jar:./onion-common.jar:./jdic_stub.jar:./httpcore-niossl-4.0-alpha7.jar:./jl.jar:./httpcore-4.0-beta2.jar:./jython.jar:./junit.jar:./foxtrot.jar
Invalid or corrupt jarfile FrostWire.jar


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_16"
Java(TM) SE Runtime Environment (build 1.6.0_16-b01)
Java HotSpot(TM) Client VM (build 14.2-b01, mixed mode, sharing)
```God.. this is getting irritating... i wanted to download like 3 songs today to complete a CD for someone.. now i can't =/.

Any other methods? or theories of why this is happening?

Edit:

Basically it's telling me "**Invalid or corrupt jarfile FrostWire.jar**" So is there something wrong with my .deb file? i downloaded it twice, still the same..

---

### Post by MelDJ on 2009-10-19
so you can set it up, but you cant run it? can you run it form applications-internet-frostwire?

---

### Post by iTheBadGuy on 2009-10-19
Yeah, i can install it without errors, but i can't open it. If i try it through Applications -> Internet -> FrostWire. it doesn't open.. and it doesn't give me a error.. it just doesn't do anything, like if i didn't click on it. That's why i tried to open it with terminal and see what the problem was..

This is frustrating, i didn't have this problem last installation :(

---

### Post by MelDJ on 2009-10-19
installed it myself just now and am having the same error. looks like we are in this together!:). let me see...

---

### Post by iTheBadGuy on 2009-10-19
ah! good, so i'm not the only one :D

---

### Post by MelDJ on 2009-10-19
try downloading the version here: [http://www.getdeb.net/release/4669](http://www.getdeb.net/release/4669)

---

### Post by iTheBadGuy on 2009-10-19
Ok thanks. Did this fix the problem for you?

---

### Post by MelDJ on 2009-10-19
my internet's slow. so i guess you could try it out first. i am guessing the packaging was not done well in the frostwire site's .deb file

---

### Post by iTheBadGuy on 2009-10-19
> **MelDJ said:**
> my internet's slow. so i guess you could try it out first. i am guessing the packaging was not done well in the frostwire site's .deb file
You're right, it probably wasn't. This installed without problems. It asked me to upgrade it - of course i said no. It wants me to go to it's page and download the fail .deb (lol). So thanks again.

---

