---
title: "Trouble installing htk: /usr/bin/ld: cannot find -lX11"
date: 2012-06-30
forum: General Help
---

### Post by Robing Goodfellow on 2012-06-30
Greetings!

I'm trying to install the HTK 3.4.1. I'm running Precise on a 64 bit HP G62.

I've downloaded and extracted to tarball to my Home directory, ran ./configure, no problems, ran make all and got and error stating "/usr/bin/ld: cannot fond -lX11"

here's the terminal output from the make all command:

```
~/htk$ make all
(cd HTKLib && make HTKLib.a) \
	  || case "" in *k*) fail=yes;; *) exit 1;; esac;
make[1]: Entering directory `/home/richard/htk/HTKLib'
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HGraf.o HGraf.c
HGraf.c: In function &#8216;DecodeKeyPress&#8217;:
HGraf.c:179:8: warning: variable &#8216;n&#8217; set but not used [-Wunused-but-set-variable]
HGraf.c: In function &#8216;HGetEvent&#8217;:
HGraf.c:221:18: warning: variable &#8216;dummy&#8217; set but not used [-Wunused-but-set-variable]
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o esig_asc.o esig_asc.c
esig_asc.c: In function &#8216;ReadAsciiEscape&#8217;:
esig_asc.c:2025:16: warning: ignoring return value of &#8216;fscanf&#8217;, declared with attribute warn_unused_result [-Wunused-result]
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o esig_edr.o esig_edr.c
esig_edr.c: In function &#8216;ReadEdrRecord&#8217;:
esig_edr.c:338:25: warning: &#8216;flags&#8217; may be used uninitialized in this function [-Wuninitialized]
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o esignal.o esignal.c
esignal.c: In function &#8216;GetLine&#8217;:
esignal.c:1760:9: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result [-Wunused-result]
esignal.c: In function &#8216;GetLong&#8217;:
esignal.c:1808:9: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result [-Wunused-result]
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o esig_nat.o esig_nat.c
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HAdapt.o HAdapt.c
HAdapt.c: In function &#8216;SetSemiTiedAvCov&#8217;:
HAdapt.c:1381:15: warning: variable &#8216;si&#8217; set but not used [-Wunused-but-set-variable]
HAdapt.c: In function &#8216;ParseNode&#8217;:
HAdapt.c:1550:12: warning: variable &#8216;size&#8217; set but not used [-Wunused-but-set-variable]
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HArc.o HArc.c
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HAudio.o HAudio.c
HAudio.c: In function &#8216;StartAudioInput&#8217;:
HAudio.c:2174:11: warning: ignoring return value of &#8216;read&#8217;, declared with attribute warn_unused_result [-Wunused-result]
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HDict.o HDict.c
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HExactMPE.o HExactMPE.c
HExactMPE.c: In function &#8216;DoCorrectness&#8217;:
HExactMPE.c:288:58: warning: value computed is not used [-Wunused-value]
HExactMPE.c:332:12: warning: variable &#8216;cb&#8217; set but not used [-Wunused-but-set-variable]
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HFB.o HFB.c
HFB.c: In function &#8216;Setotprob&#8217;:
HFB.c:999:15: warning: variable &#8216;p&#8217; set but not used [-Wunused-but-set-variable]
HFB.c: In function &#8216;SetBeta&#8217;:
HFB.c:1161:12: warning: variable &#8216;hset&#8217; set but not used [-Wunused-but-set-variable]
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HFBLat.o HFBLat.c
HFBLat.c: In function &#8216;StepAlpha&#8217;:
HFBLat.c:737:20: warning: variable &#8216;transP&#8217; set but not used [-Wunused-but-set-variable]
HFBLat.c: In function &#8216;DoAllMixUpdates&#8217;:
HFBLat.c:1070:33: warning: variable &#8216;al_otvs&#8217; set but not used [-Wunused-but-set-variable]
HFBLat.c: In function &#8216;UpMixParms&#8217;:
HFBLat.c:1198:25: warning: variable &#8216;vSize&#8217; set but not used [-Wunused-but-set-variable]
HFBLat.c: In function &#8216;StepForward&#8217;:
HFBLat.c:1389:25: warning: variable &#8216;bqt1&#8217; set but not used [-Wunused-but-set-variable]
HFBLat.c: In function &#8216;DoAllMixUpdates&#8217;:
HFBLat.c:1175:30: warning: &#8216;mammi&#8217; may be used uninitialized in this function [-Wuninitialized]
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HLabel.o HLabel.c
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HLat.o HLat.c
HLat.c: In function &#8216;LatSetScores&#8217;:
HLat.c:690:14: warning: variable &#8216;best&#8217; set but not used [-Wunused-but-set-variable]
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HLM.o HLM.c
HLM.c: In function &#8216;WriteNGrams&#8217;:
HLM.c:235:16: warning: variable &#8216;N&#8217; set but not used [-Wunused-but-set-variable]
HLM.c: In function &#8216;ReadNGrams&#8217;:
HLM.c:379:18: warning: variable &#8216;size&#8217; set but not used [-Wunused-but-set-variable]
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HMap.o HMap.c
HMap.c: In function &#8216;TotMixInSet&#8217;:
HMap.c:384:10: warning: variable &#8216;hmm&#8217; set but not used [-Wunused-but-set-variable]
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HMath.o HMath.c
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HMem.o HMem.c
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HModel.o HModel.c
HModel.c: In function &#8216;CompressItemList&#8217;:
HModel.c:1149:11: warning: variable &#8216;p&#8217; set but not used [-Wunused-but-set-variable]
HModel.c: In function &#8216;CreateHMM&#8217;:
HModel.c:4225:12: warning: variable &#8216;newMacro&#8217; set but not used [-Wunused-but-set-variable]
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HNet.o HNet.c
HNet.c: In function &#8216;CreateXEModels&#8217;:
HNet.c:3144:36: warning: variable &#8216;searchNode&#8217; set but not used [-Wunused-but-set-variable]
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HParm.o HParm.c
HParm.c: In function &#8216;SetWaveSpDetParms’:
HParm.c:2584:18: warning: variable &#8216;nBl&#8217; set but not used [-Wunused-but-set-variable]
HParm.c:2582:11: warning: variable &#8216;v&#8217; set but not used [-Wunused-but-set-variable]
HParm.c: In function &#8216;CompressPBlock&#8217;:
HParm.c:4945:16: warning: variable &#8216;count&#8217; set but not used [-Wunused-but-set-variable]
HParm.c: In function &#8216;OpenAsChannel&#8217;:
HParm.c:4351:25: warning: &#8216;initRows&#8217; may be used uninitialized in this function [-Wuninitialized]
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HRec.o HRec.c
HRec.c: In function &#8216;LatFromPaths&#8217;:
HRec.c:1650:33: warning: &#8216;labid&#8217; may be used uninitialized in this function [-Wuninitialized]
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HShell.o HShell.c
HShell.c: In function &#8216;KeyPressed&#8217;:
HShell.c:1489:14: warning: ignoring return value of &#8216;read&#8217;, declared with attribute warn_unused_result [-Wunused-result]
HShell.c: In function &#8216;NextArg&#8217;:
HShell.c:725:13: warning: ignoring return value of &#8216;strtod&#8217;, declared with attribute warn_unused_result [-Wunused-result]
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HSigP.o HSigP.c
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HTrain.o HTrain.c
HTrain.c: In function &#8216;RestoreAccsParallel&#8217;:
HTrain.c:1716:12: warning: variable &#8216;size&#8217; set but not used [-Wunused-but-set-variable]
HTrain.c: In function &#8216;InitClustering&#8217;:
HTrain.c:755:22: warning: &#8216;cov.var&#8217; may be used uninitialized in this function [-Wuninitialized]
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HUtil.o HUtil.c
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HVQ.o HVQ.c
HVQ.c: In function &#8216;LoadVQTab&#8217;:
HVQ.c:199:9: warning: &#8216;cov.var&#8217; may be used uninitialized in this function [-Wuninitialized]
HVQ.c:169:15: note: &#8216;cov.var&#8217; was declared here
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HWave.o HWave.c
HWave.c: In function &#8216;GetAIFFHeaderInfo&#8217;:
HWave.c:997:22: warning: variable &#8216;commchunk1&#8217; set but not used [-Wunused-but-set-variable]
HWave.c: In function &#8216;GetWAVHeaderInfo&#8217;:
HWave.c:1062:9: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result [-Wunused-result]
HWave.c:1068:9: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result [-Wunused-result]
HWave.c:1069:9: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result [-Wunused-result]
HWave.c:1081:12: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result [-Wunused-result]
HWave.c:1082:12: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result [-Wunused-result]
HWave.c:1087:15: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result [-Wunused-result]
HWave.c:1097:15: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result [-Wunused-result]
HWave.c:1105:15: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result [-Wunused-result]
HWave.c:1108:15: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result [-Wunused-result]
HWave.c:1109:15: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result [-Wunused-result]
HWave.c:1110:15: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result [-Wunused-result]
HWave.c:1125:33: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result [-Wunused-result]
HWave.c: In function &#8216;PutESIGHeaderInfo&#8217;:
HWave.c:1379:21: warning: &#8216;inList&#8217; may be used uninitialized in this function [-Wuninitialized]
HWave.c: In function &#8216;OpenWaveInput&#8217;:
HWave.c:1042:18: warning: &#8216;commchunk2.nSamples&#8217; may be used uninitialized in this function [-Wuninitialized]
HWave.c:998:22: note: &#8216;commchunk2.nSamples&#8217; was declared here
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o strarr.o strarr.c
if [ -f HTKLib.a ] ; then  /bin/rm HTKLib.a ; fi
ar rv HTKLib.a HGraf.o esig_asc.o esig_edr.o esignal.o esig_nat.o HAdapt.o HArc.o HAudio.o HDict.o HExactMPE.o HFB.o HFBLat.o HLabel.o HLat.o HLM.o HMap.o HMath.o HMem.o HModel.o HNet.o HParm.o HRec.o HShell.o HSigP.o HTrain.o HUtil.o HVQ.o HWave.o strarr.o
ar: creating HTKLib.a
a - HGraf.o
a - esig_asc.o
a - esig_edr.o
a - esignal.o
a - esig_nat.o
a - HAdapt.o
a - HArc.o
a - HAudio.o
a - HDict.o
a - HExactMPE.o
a - HFB.o
a - HFBLat.o
a - HLabel.o
a - HLat.o
a - HLM.o
a - HMap.o
a - HMath.o
a - HMem.o
a - HModel.o
a - HNet.o
a - HParm.o
a - HRec.o
a - HShell.o
a - HSigP.o
a - HTrain.o
a - HUtil.o
a - HVQ.o
a - HWave.o
a - strarr.o
ranlib HTKLib.a
make[1]: Leaving directory `/home/richard/htk/HTKLib'
(cd HTKTools && make all) \
	  || case "" in *k*) fail=yes;; *) exit 1;; esac;
make[1]: Entering directory `/home/richard/htk/HTKTools'
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
if [ xHSLab = xHSLab ] ; then \
		gcc -o HSLab -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HSLab.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
		else \
		gcc -o HSLab -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HSLab.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
HSLab.c: In function &#8216;FileExists&#8217;:
HSLab.c:1209:12: warning: variable &#8216;isEXF&#8217; set but not used [-Wunused-but-set-variable]
HSLab.c: In function &#8216;DoSpecial&#8217;:
HSLab.c:1596:13: warning: ignoring return value of &#8216;system&#8217;, declared with attribute warn_unused_result [-Wunused-result]
/usr/bin/ld: cannot find -lX11
collect2: ld returned 1 exit status
make[1]: *** [HSLab] Error 1
make[1]: Leaving directory `/home/richard/htk/HTKTools'
make: *** [htktools] Error 1

```

I looked in my /usr/bin directory, not ld, but there is an X11 file in there.  Is this a path issue?  I'm a little lost.

regards, Richard

---

### Post by robertfromont on 2012-07-02
I tried the following and it worked for me:

```
sudo ln -s /usr/lib/i386-linux-gnu/libX11.so.6.3.0 /usr/lib32/libX11.so
```

---

### Post by Robing Goodfellow on 2012-07-02
Awesome, worked like a champ, thanks so very much!  Now, since I'm still relatively new to this (shell commands and scripts), can you tell me what it all means? :p

regards, Richard

---

### Post by thara on 2012-08-04
can any1 help me 
i did make install and came across these errors
pls help :)


if [ ! -d /usr/local/bin ] ; then mkdir /usr/local/bin ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
if [ xHSLab = xHSLab ] ; then \
        gcc -o HSLab -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HSLab.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
        else \
        gcc -o HSLab -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HSLab.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
HSLab.c: In function &#8216;FileExists&#8217;:
HSLab.c:1209:12: warning: variable &#8216;isEXF&#8217; set but not used [-Wunused-but-set-variable]
HSLab.c: In function &#8216;DoSpecial&#8217;:
HSLab.c:1596:13: warning: ignoring return value of &#8216;system&#8217;, declared with attribute warn_unused_result [-Wunused-result]
/usr/bin/ld: cannot find -lX11
collect2: ld returned 1 exit status
make: *** [HSLab] Error 1

---

### Post by clasikowski on 2012-10-27
just look 2 posts above...

It is just one error, you can ignore the warnings.

---

### Post by pagar on 2012-11-05
Hi,
I am trying to install HTK-3.4.1 on ubuntu and having a similar error like above and I have even tried creating symbolic link but it says files exists.
Can someone help me?



(cd HTKTools && make all) \
      || case "" in *k*) fail=yes;; *) exit 1;; esac;
make[1]: Entering directory `/home/prateek/Downloads/htk/HTKTools'
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
if [ xHSLab = xHSLab ] ; then \
        gcc -o HSLab -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HSLab.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
        else \
        gcc -o HSLab -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HSLab.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
HSLab.c: In function ‘FileExists’:
HSLab.c:1209:12: warning: variable ‘isEXF’ set but not used [-Wunused-but-set-variable]
HSLab.c: In function ‘DoSpecial’:
HSLab.c:1596:13: warning: ignoring return value of ‘system’, declared with attribute warn_unused_result [-Wunused-result]
/usr/bin/ld: cannot find -lX11
collect2: ld returned 1 exit status
make[1]: *** [HSLab] Error 1
make[1]: Leaving directory `/home/prateek/Downloads/htk/HTKTools'
make: *** [htktools] Error 1
prateek@ubuntu:~/Downloads/htk$ sudo ln -s /usr/lib/i386-linux-gnu/libX11.so.6.3.0 /usr/lib32/libX11.so
[sudo] password for prateek: 
ln: failed to create symbolic link `/usr/lib32/libX11.so': File exists

---

