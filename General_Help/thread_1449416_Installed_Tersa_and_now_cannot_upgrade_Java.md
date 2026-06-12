---
title: "Installed Tersa and now cannot upgrade Java"
date: 2010-04-07
forum: General Help
---

### Post by giancast on 2010-04-07
Hello everybody I installed Tersa (graphical web dev app) over the weekend and when the update manager found some updates it could not install the Java packages. I got the message that Java is also used in Tersa so it could not be upgraded. I then tried to unistall Tersa and I cannot with the same message. I tried using the command line and this is what I get:

[COLOR="Red"]giancarlo64@giancarlo64-desktop:~$ sudo apt-get remove tersus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-bin: Depends: sun-java6-jre (= 6-16-0ubuntu1.9.04) but 6.19-0ubuntu1.9.04 is to be installed
  sun-java6-jre: Depends: sun-java6-bin (= 6.19-0ubuntu1.9.04) but 6-16-0ubuntu1.9.04 is to be installed or
                          ia32-sun-java6-bin (= 6.19-0ubuntu1.9.04) but it is not going to be installed
  sun-java6-plugin: Depends: sun-java6-bin (= 6.19-0ubuntu1.9.04) but 6-16-0ubuntu1.9.04 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
giancarlo64@giancarlo64-desktop:~$ [/COLOR]

This message is similar to what I get in Synaptic Package Manager.
First I get You have 3 broken packages on your system. Use the "Broken" filter to locate them.

Once I locate them, they are:
sun-java6-bin
sun-java6-jre
sun-java6-plugin, I can only mark for upgrade the first one.
When I say upgrade I get E:/var/cache/apt/archivessun-java6-bin_6.19-0ubuntu1.9.04_amd64.deb:trying to overwrite 'usr/lib/jvm/java-6-sun', which is also in package tersus
When I expand the details this is what is inside:
see attachment.
When I try to remove Tersus I get the same window with the above erroe E:/var/cache/apt..................in package tersus.

Any help will be greatly appreciated.

Thanks

---

### Post by johnaaronrose on 2010-04-20
From another thread, try:
 				 				**Re: Sypnatic Problems** 			
 			 			 		   		 		 		Open up Synaptic. System-Administration-Synaptic Package Manager. On the lower left click on custom filters, on the top left click on broken. Is anything listed? Go to Edit-Fix Broken Packages and finally click reload. 

Failing the above, try from another thread:
In case of these packages (i.e. sun-java6-bin sun-java6-jre), my bet is that when you installed them you didn't accept the EULA that the Java installer pops up. And without accepting it the package installation couldn't continue, thus the packages broke.


You could try running something like "sudo dpkg-reconfigure sun-java6-bin sun-java6-jre", or just removing and then installing the packages again. And in case I was right and you missed the EULA, accept it this time (it opens in a terminal window, and you need to press TAB key to select the "accept"-button and then press enter.)

---

### Post by MrTres on 2010-05-06
**Edit: Updating to 10.4 Lucid Lynx resolved the issue for me..**

I have the same problem.

When I try to run the updater, I get the following error:

```
E: /var/cache/apt/archives/sun-java6-bin_6.20dlj-0ubuntu1.9.10_amd64.deb: trying to overwrite '/usr/lib/jvm/java-6-sun', which is also in package tersus 0
```And the details are (some parts are Danish):

```
Prækonfigurerer pakker ...
(Læser database... 407672 filer og mapper aktuelt installeret.)
Gør klar til at erstatte sun-java6-bin 6-16-0ubuntu1.9.04 (med .../sun-java6-bin_6.20dlj-0ubuntu1.9.10_amd64.deb)...
sun-dlj-v1-1 license has already been accepted
Udpakker erstatning sun-java6-bin...
dpkg: fejl under behandling af /var/cache/apt/archives/sun-java6-bin_6.20dlj-0ubuntu1.9.10_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/jvm/java-6-sun', which is also in package tersus 0:1.3.43
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
Der opstod fejl under behandlingen:
 /var/cache/apt/archives/sun-java6-bin_6.20dlj-0ubuntu1.9.10_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: afhængighedsproblemer forhindrer konfiguration af sun-java6-jre:
 sun-java6-jre afhænger af sun-java6-bin (= 6.20dlj-0ubuntu1.9.10) | ia32-sun-java6-bin (= 6.20dlj-0ubuntu1.9.10), men:
  Version af sun-java6-bin på systemet er 6-16-0ubuntu1.9.04.
  Pakken 'ia32-sun-java6-bin' er ikke installeret.
dpkg: fejl under behandling af sun-java6-jre (--configure):
 afhængighedsproblemer - efterlader den ukonfigureret
dpkg: afhængighedsproblemer forhindrer konfiguration af sun-java6-jdk:
 sun-java6-jdk afhænger af sun-java6-bin (= 6.20dlj-0ubuntu1.9.10), men:
  Version af sun-java6-bin på systemet er 6-16-0ubuntu1.9.04.
dpkg: fejl under behandling af sun-java6-jdk (--configure):
 afhængighedsproblemer - efterlader den ukonfigureret
Der opstod fejl under behandlingen:
 sun-java6-jre
 sun-java6-jdk
```I've tried doing the suggested thing with the Synaptic Package Manager to fix broken packages, but it gives the same error message as above. I've tried the dpkg-reconfigure as well, it gives me this output:

```
torin@torin-laptop:~$ sudo dpkg-reconfigure sun-java6-bin sun-java6-jdk sun-java6-jre 
/usr/sbin/dpkg-reconfigure: sun-java6-jdk har brudte afhængigheder eller ikke fuldt installeret
```(sun-java6-jdk has broken dependencies or is not fully/completely installed)

I've tried removing tersus:

```
torin@torin-laptop:~$ sudo apt-get remove tersus 
Indlæser pakkelisterne... Færdig
Opbygger afhængighedstræ        
Læser tilstandsoplysninger... Færdig
Du kan muligvis rette det ved at køre 'apt-get -f install':
Følgende pakker har uopfyldte afhængigheder:
  sun-java6-bin: Afhængigheder: sun-java6-jre (= 6-16-0ubuntu1.9.04) men 6.20dlj-0ubuntu1.9.10 forventes installeret
  sun-java6-jdk: Afhængigheder: sun-java6-bin (= 6.20dlj-0ubuntu1.9.10) men 6-16-0ubuntu1.9.04 forventes installeret
  sun-java6-jre: Afhængigheder: sun-java6-bin (= 6.20dlj-0ubuntu1.9.10) men 6-16-0ubuntu1.9.04 forventes installeret eller
                                 ia32-sun-java6-bin (= 6.20dlj-0ubuntu1.9.10) men den bliver ikke installeret
E: Uopfyldte afhængigheder. Prøv 'apt-get -f install' uden pakker (eller angiv en løsning).
```The error message translates to "Broken dependencies. Try '...' without packages". If I try to remove either or all of the sun-java6 packages, I get the same error / suggestion. So I tried that:


```
torin@torin-laptop:~$ sudo apt-get -f install
Indlæser pakkelisterne... Færdig
Opbygger afhængighedstræ        
Læser tilstandsoplysninger... Færdig
Retter afhængigheder... Færdig
Følgende yderligere pakker vil blive installeret:
  sun-java6-bin
Følgende pakker vil blive opgraderet:
  sun-java6-bin
1 opgraderes, 0 nyinstalleres, 0 afinstalleres og 14 opgraderes ikke.
2 ikke fuldstændigt installerede eller afinstallerede.
0B/27,7MB skal hentes fra arkiverne.
After this operation, 1.024kB of additional disk space will be used.
Vil du fortsætte [J/n]? J
Prækonfigurerer pakker ...
(Læser database... 407672 filer og mapper aktuelt installeret.)
Gør klar til at erstatte sun-java6-bin 6-16-0ubuntu1.9.04 (med .../sun-java6-bin_6.20dlj-0ubuntu1.9.10_amd64.deb)...
sun-dlj-v1-1 license has already been accepted
Udpakker erstatning sun-java6-bin...
dpkg: fejl under behandling af /var/cache/apt/archives/sun-java6-bin_6.20dlj-0ubuntu1.9.10_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/jvm/java-6-sun', which is also in package tersus 0:1.3.43
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
Der opstod fejl under behandlingen:
 /var/cache/apt/archives/sun-java6-bin_6.20dlj-0ubuntu1.9.10_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```(But i figure this is the same as doing it through the Package Manager.)

So it would seem I can remove neither tersus nor java, and I can't upgrade java either.. What to do?

**Edit: Updating to 10.4 Lucid Lynx resolved the issue for me..**

Thanks for your time!
/MrTres

---

