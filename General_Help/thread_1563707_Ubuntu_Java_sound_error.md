---
title: "Ubuntu Java sound error"
date: 2010-08-29
forum: General Help
---

### Post by TTGRULES on 2010-08-29
ubuntu 10.04 LTS

HP dv7-3078nr

I am signed up for an online class and their classroom keeps returning an error for the voip function. It is java based, and the sound in Java works fine on other applications. I have googled the problem in every possible way I can think of with no result. I have checked the alsa configuration and installed java-6 from the partners repository... still no luck.... the error looks something like this: 


Sun Aug 29 14:00:48 EDT 2010 - [debug] IAX_ERR Expression 'PaAlsaStreamComponent_InitialConfigure( &self->capture, inParams, self->primeBuffers, hwParamsCapture, &realSr )' failed in '/home/buildbot/ct-ubuntu-7.10/coretech-trunk-ubuntu-7.10/build/portaudio/src/hostapi/alsa/pa_linux_alsa.c', line: 1876
Sun Aug 29 14:00:48 EDT 2010 - [debug] IAX_ERR Expression 'PaAlsaStream_Configure( stream, inputParameters, outputParameters, sampleRate, framesPerBuffer, &inputLatency, &outputLatency, &hostBufferSizeMode )' failed in '/home/buildbot/ct-ubuntu-7.10/coretech-trunk-ubuntu-7.10/build/portaudio/src/hostapi/alsa/pa_linux_alsa.c', line: 2000
Sun Aug 29 14:00:48 EDT 2010 - [debug] IAX_ERR PortAudio error at Unable to open streams: Invalid error code (value greater than zero)
Sun Aug 29 14:00:48 EDT 2010 - [debug] IAX_ERR IAXCLIENT: failed to service audio
Sun Aug 29 14:00:49 EDT 2010 - [debug] IAX_ERR Expression 'SetApproximateSampleRate( pcm, hwParams, sr )' failed in '/home/buildbot/ct-ubuntu-7.10/coretech-trunk-ubuntu-7.10/build/portaudio/src/hostapi/alsa/pa_linux_alsa.c', line: 1305
Sun Aug 29 14:00:49 EDT 2010 - [debug] IAX_OUT iaxc_ev_text	-1	2	failed to service audio
Sun Aug 29 14:00:49 EDT 2010 - [debug] IAX_ERR Expression 'PaAlsaStreamComponent_InitialConfigure( &self->capture, inParams, self->primeBuffers, hwParamsCapture, &realSr )' failed in '/home/buildbot/ct-ubuntu-7.10/coretech-trunk-ubuntu-7.10/build/portaudio/src/hostapi/alsa/pa_linux_alsa.c', line: 1876
Sun Aug 29 14:00:49 EDT 2010 - [debug] IAX_ERR Expression 'PaAlsaStream_Configure( stream, inputParameters, outputParameters, sampleRate, framesPerBuffer, &inputLatency, &outputLatency, &hostBufferSizeMode )' failed in '/home/buildbot/ct-ubuntu-7.10/coretech-trunk-ubuntu-7.10/build/portaudio/src/hostapi/alsa/pa_linux_alsa.c', line: 2000
Sun Aug 29 14:00:49 EDT 2010 - [debug] IAX_ERR PortAudio error at Unable to open streams: Invalid error code (value greater than zero)
Sun Aug 29 14:00:49 EDT 2010 - [debug] IAX_ERR IAXCLIENT: failed to service audio
Sun Aug 29 14:00:49 EDT 2010 - [info] iax notice, msg => failed to service audio



These lines just keep repeating themselves. It seems to refer to a directory on my computer that is non existant... I have tried multiple ways of finding it with no luck... any help would be great!!!

---

### Post by TTGRULES on 2010-08-29
Bump....... Anyone there????

---

### Post by tgoff on 2010-08-30
I am having the same issue.  I am also running Win XP in side of Sun Virtual box and the online class software works fine.  The sound is able to get through to the guest OS with no problem, but running in Ubuntu, no dice... 

Like you, I havent been able to find anything via googling.  Im trying to debug myself and will let you know what I find out.  


The online class framework that I am using is Horizon Wimba media 

Tim

---

### Post by tgoff on 2010-08-30
this is the relevant log segment that I am seeing:

[debug] IAX_ERR HZTC tunneling initialized 
[debug] IAX_ERR Expression 'SetApproximateSampleRate( pcm, hwParams, sr )' failed in '/home/buildbot/ct-ubuntu-7.10/coretech-trunk-ubuntu-7.10/build/portaudio/src/hostapi/alsa/pa_linux_alsa.c', line: 1305
[debug] IAX_ERR Expression 'PaAlsaStreamComponent_InitialConfigure( &self->capture, inParams, self->primeBuffers, hwParamsCapture, &realSr )' failed in '/home/buildbot/ct-ubuntu-7.10/coretech-trunk-ubuntu-7.10/build/portaudio/src/hostapi/alsa/pa_linux_alsa.c', line: 1876
[debug] IAX_ERR Expression 'PaAlsaStream_Configure( stream, inputParameters, outputParameters, sampleRate, framesPerBuffer, &inputLatency, &outputLatency, &hostBufferSizeMode )' failed in '/home/buildbot/ct-ubuntu-7.10/coretech-trunk-ubuntu-7.10/build/portaudio/src/hostapi/alsa/pa_linux_alsa.c', line: 2000
[debug] IAX_ERR PortAudio error at Unable to open streams: Invalid error code (value greater than zero)
[debug] IAX_ERR using vidcap sapi Video for Linux (v4l) video capture API (video4linux)
[debug] IAX_ERR Expression 'SetApproximateSampleRate( pcm, hwParams, sr )' failed in '/home/buildbot/ct-ubuntu-7.10/coretech-trunk-ubuntu-7.10/build/portaudio/src/hostapi/alsa/pa_linux_alsa.c', line: 1305
[debug] IAX_ERR Expression 'PaAlsaStreamComponent_InitialConfigure( &self->capture, inParams, self->primeBuffers, hwParamsCapture, &realSr )' failed in '/home/buildbot/ct-ubuntu-7.10/coretech-trunk-ubuntu-7.10/build/portaudio/src/hostapi/alsa/pa_linux_alsa.c', line: 1876
[debug] IAX_ERR Expression 'PaAlsaStream_Configure( stream, inputParameters, outputParameters, sampleRate, framesPerBuffer, &inputLatency, &outputLatency, &hostBufferSizeMode )' failed in '/home/buildbot/ct-ubuntu-7.10/coretech-trunk-ubuntu-7.10/build/portaudio/src/hostapi/alsa/pa_linux_alsa.c', line: 2000
[debug] IAX_ERR PortAudio error at Unable to open streams: Invalid error code (value greater than zero)
[debug] IAX_ERR Starting console thread


(there were timestamps in there as well, but I removed them to diff this log with one from a successful run on Win XP in the virtual machine.)  

later on, the same messages get repeated a bunch of times, but this seems to be the first sign of trouble.  This instance came from executing the Wimba set up wizard.  while running this wizard, I was not able to get any sound.  

The lines above do not have a similar entry in the windows log, so this appears to be linux specific code, not platform independent Wimba code.  based on the filenames etc, this appears to be related to either pulse audio, ALSA, or the iaxcomm softphone framework.  

that is all I have for now.

---

### Post by tgoff on 2010-08-31
few more things before calling it a nite.  the non existent paths in the error are the paths to the source code when the binary was compiled.  I am guessing that the original poster is using Wimba media for their course.  if so, the binary which is called by the browser to start the class session is at something like ~/.horizonwimba/JSecureDoor/horizonmedia_2.3./data/horizonmedia (it gets installed the first time you try to run the setup wizard).  Inside of that executable are error codes for various errors which contain the source file and line number.  unfortunately, those source files are absolute paths in the build system and not too useful to the end user, except in telling you what source the error is in.  I found a version of the file causing the errors at [http://code.google.com/p/pcsx2/source/browse/trunk/3rdparty/portaudio/src/hostapi/alsa/pa_linux_alsa.c?spec=svn2894&r=2894](http://code.google.com/p/pcsx2/source/browse/trunk/3rdparty/portaudio/src/hostapi/alsa/pa_linux_alsa.c?spec=svn2894&r=2894) , but it is not the exact right version as some of the line numbers are off (line numbers in errors do not correspond to what is actually at those line numbers, but seem close).  It seems that the error is due to this function call: SetApproximateSampleRate( pcm, hwParams, sr ).  I have tried running this in a debugger, but have not been able to get the values of the actual variables.  I will try to find and download the correct source file to help make debugging simpler tomorrow.

---

### Post by tgoff on 2010-08-31
I have created a ticket with Wimba.  the ticket is available at [http://d2.parature.com/ics/support/default.asp?deptID=8052&ticketID=9191692](http://d2.parature.com/ics/support/default.asp?deptID=8052&ticketID=9191692) but you apparently have to create an account and login to view it.  I haven't had much more success, except that I saw the same symptoms (no audio in the wizard) without the same errors.  I did see a java exception in the log file that you can get to within the wizard window, but not in the log that is written under ~/.horizonwimba.  that exception looks like:

Tue Aug 31 21:04:41 EDT 2010 - [debug] door_args => -start:target HMSCLIENT -hztc:remote umd.wimba.com:4569 -hztc:http umd.wimba.com:80 -hztc:alt_http 5998 -hztc:alt_http 5191 -hztc:udp -hztc:http_suffix /HZTunnel2/ -hztc:raw_udp 5998 -hztc:connect 5998 -hztc:raw_udp 33434 -hztc:connect 33434 -hztc:raw_udp 5191 -hztc:connect 5191 -hztc:raw_udp 16384 -hztc:connect 16384 -hztc:log_file ../logs/hztc_debug.log -hztc:log_level 4 -hmsclient:username guest -hmsclient:pin wizard-playback -jb:target-extra -1 -videocontrols:enable 0
Tue Aug 31 21:04:41 EDT 2010 - [info] successfully parsed door parameters
Tue Aug 31 21:04:41 EDT 2010 - [info] successfully initialized door
Tue Aug 31 21:04:41 EDT 2010 - [warn] unable to retrieve key from args hashmap, key => -hmsclient:skip_connect
Tue Aug 31 21:04:41 EDT 2010 - [info] skip_connect not specified
Tue Aug 31 21:04:41 EDT 2010 - [warn] unable to retrieve key from params hashmap, key => BANDWIDTHDEFAULT
Tue Aug 31 21:04:41 EDT 2010 - [debug] initializing gui
Tue Aug 31 21:04:41 EDT 2010 - [debug] initializing log window
Tue Aug 31 21:04:42 EDT 2010 - [debug] initializing look-and-feel
Tue Aug 31 21:04:42 EDT 2010 - [debug] initializing panel settings
Tue Aug 31 21:04:42 EDT 2010 - [debug] initializing buttons
Tue Aug 31 21:04:43 EDT 2010 - [warn] unable to find resource, path => /hms/speaker_icon/mic_enabled_flat.png
Tue Aug 31 21:04:43 EDT 2010 - [debug] max => 21
Tue Aug 31 21:04:43 EDT 2010 - [warn] unable to retrieve key from params hashmap, key => BANDWIDTHLOWEST
Tue Aug 31 21:04:43 EDT 2010 - [warn] unable to retrieve key from params hashmap, key => BANDWIDTHLOW
Tue Aug 31 21:04:43 EDT 2010 - [warn] unable to retrieve key from params hashmap, key => BANDWIDTHMEDIUM
Tue Aug 31 21:04:43 EDT 2010 - [warn] unable to retrieve key from params hashmap, key => BANDWIDTHHIGH
Tue Aug 31 21:04:43 EDT 2010 - [warn] unable to retrieve key from params hashmap, key => BANDWIDTHHIGHER
Tue Aug 31 21:04:43 EDT 2010 - [warn] unable to retrieve key from params hashmap, key => BANDWIDTHHIGHEST
Tue Aug 31 21:04:43 EDT 2010 - [warn] unable to retrieve key from params hashmap, key => BANDWIDTHLOWEST
Tue Aug 31 21:04:43 EDT 2010 - [warn] BandwidthWindow.init(), caught exception
java.lang.Exception: java.lang.NumberFormatException: null
	at aG.<init>(SourceFile)
	at e.a(SourceFile)
	at e.b(SourceFile)
	at o.a(SourceFile)
	at ab.<init>(SourceFile)
	at o.<init>(SourceFile)
	at M.a(SourceFile)
	at ab.<init>(SourceFile)
	at M.<init>(SourceFile)
	at t.<init>(SourceFile)
	at com.hw.clients.hms.h.<init>(SourceFile)
	at com.hw.clients.hms.HorizonMediaApplet$b.run(SourceFile)
	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:199)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)

Tue Aug 31 21:04:43 EDT 2010 - [warn] unable to retrieve key from args hashmap, key => -simulcast:number
Tue Aug 31 21:04:43 EDT 2010 - [debug] Checking if video button should be available

---

### Post by tgoff on 2010-08-31
ah, it seems like the log available in the wizard includes output from both the java plugin and the horizon media executeable.  the log on the filesystem is just the output from horizonmedia.

---

### Post by TTGRULES on 2010-09-25
Ive tried everything to get this to work and its still a no-go.. I had to use other windows computers... and virtual boxes to do my classes.... every time I use them I am reminded why I like ubuntu better... but I wish it would work with wimba media!!!

---

### Post by Kamallo on 2012-10-17
It seems to be an issue in PortAudio rather than in Wimba, depending on the audio card you have.
In my Ubuntu 12.04 (64 bit) I got it fixed by running this:

```
export PA_ALSA_PLUGHW=1
```

before running Firefox or Chrome from the terminal / command line.
After this, both audio playing and recording worked fine in Wimba.

You might want to update your issue or send an email to the Wimba support team so they know about it and other Wimba users can benefit from this knowledge.

Good luck!

-- 
Kamal

---

