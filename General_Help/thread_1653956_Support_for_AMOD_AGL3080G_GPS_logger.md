---
title: "Support for AMOD AGL3080G GPS logger"
date: 2010-12-27
forum: General Help
---

### Post by fishtoprecords on 2010-12-27
Is there a way to use the Amod AGL3080 GPS logger under Ubuntu? I'm running 10.10.

The vendor supports Windows and OS-X; I can't get the vendor's reader program to work under Wine.

Error under wine:


>  wine AmodGPSTracker.exe 
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
wine: Install the Windows version of Mono to run .NET executables


The input file looks like this:


> $GPRMC,212723.000,A,3853.3696,N,07712.0752,W,0.00,137.26,271210,,,A*79
$GPVTG,137.26,T,,M,0.00,N,0.0,K,A*0C
$GPGGA,212724.000,3853.3696,N,07712.0752,W,1,04,3.2,139.7,M,-33.5,M,,0000*6B
$GPGSA,A,3,21,26,18,15,,,,,,,,,5.7,3.2,4.7*38
$GPRMC,212724.000,A,3853.3696,N,07712.0752,W,0.00,137.26,271210,,,A*7E
$GPVTG,137.26,T,,M,0.00,N,0.0,K,A*0C
$GPGGA,212725.000,3853.3696,N,07712.0752,W,1,04,3.2,139.7,M,-33.5,M,,0000*6A
$GPGSA,A,3,21,26,18,15,,,,,,,,,5.7,3.2,4.7*38


Which does not look like it would be very hard to parse.

I've love to find a program that can process this, without having to write my own.

---

