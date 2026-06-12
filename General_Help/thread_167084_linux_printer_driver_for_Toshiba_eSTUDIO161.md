---
title: "linux printer driver for Toshiba eSTUDIO161"
date: 2006-04-27
forum: General Help
---

### Post by mircea mircea on 2006-04-27
help.
I'm a new user of Ubuntu 5.10 i386
Can somebody help me to install a network printer (Toshiba eSTUDIO161) ?
After i've tried with Mandriva and Suse, I'm give up because of problems with the other printer(HP1100A) and with the network.
Finally with Ubuntu I can print on my HP1100A and I can browse entire network.
In our network(10 XP computers+1 server with Win2000) we have an Toshiba eSTUDIO161 printer, connected to the server.
I can't find any driver for linux( after 2weeks of searching with Google).
My computer is an Duron1000Mhz, 384MB ram, Nvidia Geforce 2, Maxtor 20Gb, 3Com network adapter
Thank you.

---

### Post by nomail on 2006-05-29
I also would like to see it working in Ubuntu :-k

---

### Post by darka on 2006-06-02
I used this howto to get a windows-only printer working over network in linux:
[http://mywebpages.comcast.net/heretrythis/hp3100/psemugs.html](http://mywebpages.comcast.net/heretrythis/hp3100/psemugs.html)

---

### Post by mircea mircea on 2006-06-16
[QUOTE=darka]I used this howto to get a windows-only printer working over network in linux:
[http://mywebpages.comcast.net/heretrythis/hp3100/psemugs.html](http://mywebpages.comcast.net/heretrythis/hp3100/psemugs.html)[/QUOTE]

Thank you,
Finally somebody try to help me.
I have only one problem: 
Toshiba eStudio 161 is not a post-script printer.
But thanks anyway.

---

### Post by andrew.george.hammond on 2006-07-05
You'll need the following ppd file. Copy it into e-studio16_20_25.ppd

-------- snip ---
*PPD-Adobe: "4.3"

*% =======================================================
*%  Printer Description file
*%    for "TOSHIBA e-STUDIO16/20/25 Series" for MAC PPD file
*%    Version 1.18
*%    CreationDate: 2000/05/10
*%    Modified:     2001/04/25
*%
*%    COPYRIGHT (C) 2000-2001 TOSHIBA TEC Corp.
*%    COPYRIGHT (C) 2000-2001 DESTINY Ltd.
*%    All rights reserved.
*% =======================================================

*FormatVersion: "4.3"
*FileVersion: "1.2.0"
*LanguageVersion: English
*LanguageEncoding: ISOLatin1
*Manufacturer: "Toshiba"
*PCFileName: "TSBeST16.ppd"
*Product: "(TOSHIBA e-STUDIO16/20/25)"
*PSVersion: "(2014.108) 1"
*ModelName: "TOSHIBA e-STUDIO16/20/25"
*NickName: "TOSHIBA e-STUDIO16/20/25"
*ShortNickName: "TOSHIBA e-STUDIO16/20/25"

*LanguageLevel: "2"
*Protocols: PJL
*ColorDevice: False
*DefaultColorSpace: Gray
*TTRasterizer: Type42
*FileSystem: False
*Throughput: "17"

*OpenGroup: InstallableOptions

*OpenUI *Option1/Duplex Unit: Boolean
*DefaultOption1: False
*Option1 True/Installed: ""
*Option1 False/Not Installed: ""
*CloseUI: *Option1

*OpenUI *Option21/Cassette2: Boolean
*DefaultOption21: False
*Option21 True/Installed: " "
*Option21 False/Not Installed: ""
*CloseUI: *Option21

*OpenUI *Option20/Cassette3: Boolean
*DefaultOption20: False
*Option20 True/Installed: " "
*Option20 False/Not Installed: ""
*CloseUI: *Option20

*OpenUI *Option24/Cassette4: Boolean
*DefaultOption24: False
*Option24 True/Installed: " "
*Option24 False/Not Installed: ""
*CloseUI: *Option24

*OpenUI *Option25/Large Capacity Feeder: Boolean
*DefaultOption25: False
*Option25 True/Installed: " "
*Option25 False/Not Installed: ""
*CloseUI: *Option25

*OpenUI *Option22/Stack Feed Bypass: Boolean
*DefaultOption22: False
*Option22 True/Installed: " "
*Option22 False/Not Installed: ""
*CloseUI: *Option22

*OpenUI *Option23/Others: PickOne
*DefaultOption23: None
*Option23 None/Not Installed: ""
*Option23 Finisher/Finisher: ""
*Option23 Offset/Offset Stacker: ""
*Option23 Job/Job Separator: ""
*CloseUI: *Option23

*CloseGroup: InstallableOptions




*% LCF tray can not exist when Tray2 is not installed
*UIConstraints: *Option21 False	*Option25 True

*% Tray3 tray can not exist when Tray2 is not installed
*% Tray4 tray can not exist when Tray2 or Tray3 is not installed
*UIConstraints: *Option21 False	*Option20 True
*UIConstraints: *Option21 False	*Option24 True
*UIConstraints: *Option20 False	*Option24 True

*UIConstraints: *Option24 False *InputSlot Cassette4
*UIConstraints: *Option20 False *InputSlot Cassette3
*UIConstraints: *Option21 False *InputSlot Cassette2
*UIConstraints: *InputSlot Cassette4 *Option24 False
*UIConstraints: *InputSlot Cassette3 *Option20 False
*UIConstraints: *InputSlot Cassette2 *Option21 False

*% Tray4 and Tray3 tray can not exist when LCF is installed
*UIConstraints: *Option20 True	*Option25 True
*UIConstraints: *Option24 True	*Option25 True

*%Job Trays is disabled when Job Separator is not installed
*UIConstraints: *Option23 None *OutputBin Lower
*UIConstraints: *Option23 None *OutputBin Upper
*UIConstraints: *Option23 None *OutputBin T1
*UIConstraints: *Option23 None *OutputBin T2

*UIConstraints: *Option23 Offset *OutputBin Lower
*UIConstraints: *Option23 Offset *OutputBin Upper
*UIConstraints: *Option23 Offset *OutputBin T1
*UIConstraints: *Option23 Offset *OutputBin T2

*UIConstraints: *Option23 Job *OutputBin T1
*UIConstraints: *Option23 Job *OutputBin T2
*UIConstraints: *Option23 Finisher *OutputBin Lower
*UIConstraints: *Option23 Finisher *OutputBin Upper

*%Finisher Trays is disabled when Finisher is not installed
*UIConstraints: *Option23 Finisher *OutputBin Lower
*UIConstraints: *Option23 Finisher *OutputBin Upper

*%Offset is disabled when Offset is not installed
*UIConstraints: *Option23 None *Offset On
*UIConstraints: *Option23 Job *Offset On

*% duplex installed or not installed
*UIConstraints:  *Option1 False *Duplex DuplexS
*UIConstraints:  *Option1 False *Duplex DuplexT

*% Paper Size not work with Offset
*%UIConstraints: *Offset On	*PageSize A6
*%UIConstraints: *Offset On	*PageSize Comm10
*%UIConstraints: *Offset On	*PageSize Monarch
*UIConstraints: *Offset On	*PageSize A5
*UIConstraints: *Offset On	*PageSize Statement

*% Edge Smoothing is disable when Toner Saver is On
*UIConstraints: *Option6 On  *Option7 On

*% Paper Type not work with Job Upper
*UIConstraints: *OutputBin	Upper		*PaperType Envelopes
*UIConstraints: *OutputBin	Upper		*PaperType Transparencies
*UIConstraints: *OutputBin	Upper		*PaperType Labels
*UIConstraints: *OutputBin	Upper		*PaperType Cardstocks

*% Paper Type not work with Offset
*UIConstraints: *Offset On	*PaperType Envelopes
*UIConstraints: *Offset On	*PaperType Transparencies
*UIConstraints: *Offset On	*PaperType Labels
*UIConstraints: *Offset On	*PaperType Cardstocks

*% Paper Type not work with Duplex
*UIConstraints: *Duplex DuplexS	*PaperType Envelopes
*UIConstraints: *Duplex DuplexS	*PaperType Transparencies
*UIConstraints: *Duplex DuplexS	*PaperType Labels
*UIConstraints: *Duplex DuplexS	*PaperType Cardstocks
*UIConstraints: *Duplex DuplexT	*PaperType Envelopes
*UIConstraints: *Duplex DuplexT	*PaperType Transparencies
*UIConstraints: *Duplex DuplexT	*PaperType Labels
*UIConstraints: *Duplex DuplexT	*PaperType Cardstocks

*% Paper Type not work with tray1-4 & LCF
*UIConstraints: *InputSlot Cassette1	*PaperType Envelopes
*UIConstraints: *InputSlot Cassette1	*PaperType Transparencies
*UIConstraints: *InputSlot Cassette1	*PaperType Labels
*UIConstraints: *InputSlot Cassette1	*PaperType Cardstocks
*UIConstraints: *InputSlot Cassette2	*PaperType Envelopes
*UIConstraints: *InputSlot Cassette2	*PaperType Transparencies
*UIConstraints: *InputSlot Cassette2	*PaperType Labels
*UIConstraints: *InputSlot Cassette2	*PaperType Cardstocks
*UIConstraints: *InputSlot Cassette3	*PaperType Envelopes
*UIConstraints: *InputSlot Cassette3	*PaperType Transparencies
*UIConstraints: *InputSlot Cassette3	*PaperType Labels
*UIConstraints: *InputSlot Cassette3	*PaperType Cardstocks
*UIConstraints: *InputSlot Cassette4	*PaperType Envelopes
*UIConstraints: *InputSlot Cassette4	*PaperType Transparencies
*UIConstraints: *InputSlot Cassette4	*PaperType Labels
*UIConstraints: *InputSlot Cassette4	*PaperType Cardstocks
*UIConstraints: *InputSlot LCF		*PaperType Envelopes
*UIConstraints: *InputSlot LCF		*PaperType Transparencies
*UIConstraints: *InputSlot LCF		*PaperType Labels
*UIConstraints: *InputSlot LCF		*PaperType Cardstocks

*UIConstraints: *InputSlot Auto	*PaperType Cardstocks
*UIConstraints: *InputSlot Auto	*PaperType Envelopes
*UIConstraints: *InputSlot Auto	*PaperType Transparencies
*UIConstraints: *InputSlot Auto	*PaperType Labels
*UIConstraints: *InputSlot Auto	*PaperType Cardstocks

*% Paper Type is disabled when Bypass Tray is not installed
*UIConstraints: *Option22 False	*PaperType Envelopes
*UIConstraints: *Option22 False	*PaperType Transparencies
*UIConstraints: *Option22 False	*PaperType Labels
*UIConstraints: *Option22 False	*PaperType Cardstocks

*% Bypass Tray is disabled when Bypass Tray is not installed
*UIConstraints: *Option22 False        *InputSlot Manual
*%UIConstraints: *Option22 False        *PageSize A6
*%UIConstraints: *Option22 False        *PageSize Comm10
*%UIConstraints: *Option22 False        *PageSize Monarch

*% LCF Tray is disabled when LCF is not installed
*UIConstraints: *Option25 False	*InputSlot LCF

*% LCF don't support lots of paper size.
*UIConstraints: *InputSlot LCF	*PageSize A3
*UIConstraints: *InputSlot LCF	*PageSize A5
*%UIConstraints: *InputSlot LCF	 *PageSize A6
*UIConstraints: *InputSlot LCF	*PageSize B4-JIS
*UIConstraints: *InputSlot LCF	*PageSize B5-JIS
*UIConstraints: *InputSlot LCF	*PageSize Ledger
*UIConstraints: *InputSlot LCF	*PageSize Legal
*%UIConstraints: *InputSlot LCF	 *PageSize 13Legal
*UIConstraints: *InputSlot LCF	*PageSize Statement
*UIConstraints: *InputSlot LCF	*PageSize Computer
*UIConstraints: *InputSlot LCF	*PageSize Folio
*%UIConstraints: *InputSlot LCF	 *PageSize Monarch
*%UIConstraints: *InputSlot LCF	 *PageSize Comm10

*UIConstraints:	*PageSize A3		 *InputSlot LCF
*UIConstraints:	*PageSize A5		 *InputSlot LCF
*%UIConstraints:	*PageSize A6		 *InputSlot LCF
*UIConstraints:	*PageSize B4-JIS	 *InputSlot LCF
*UIConstraints:	*PageSize B5-JIS	 *InputSlot LCF
*UIConstraints:	*PageSize Ledger	 *InputSlot LCF
*UIConstraints:	*PageSize Legal		 *InputSlot LCF
*%UIConstraints:	*PageSize 13Legal	 *InputSlot LCF
*UIConstraints:	*PageSize Statement	 *InputSlot LCF
*UIConstraints:	*PageSize Computer	 *InputSlot LCF
*UIConstraints:	*PageSize Folio		 *InputSlot LCF
*%UIConstraints:	*PageSize Monarch	 *InputSlot LCF
*%UIConstraints:	*PageSize Comm10	 *InputSlot LCF

*% paper size not work with tray1-4 and Duplex
*%UIConstraints: *PageSize A6        *InputSlot Cassette1
*%UIConstraints: *PageSize A6        *InputSlot Cassette2
*%UIConstraints: *PageSize A6        *InputSlot Cassette3
*%UIConstraints: *PageSize A6        *InputSlot Cassette4
*%UIConstraints: *PageSize A6        *Duplex DuplexS
*%UIConstraints: *PageSize A6        *Duplex DuplexT
*%UIConstraints: *PageSize Comm10        *InputSlot Cassette1
*%UIConstraints: *PageSize Comm10        *InputSlot Cassette2
*%UIConstraints: *PageSize Comm10        *InputSlot Cassette3
*%UIConstraints: *PageSize Comm10        *InputSlot Cassette4
*%UIConstraints: *PageSize Comm10        *Duplex DuplexS
*%UIConstraints: *PageSize Comm10        *Duplex DuplexT
*%UIConstraints: *PageSize Monarch        *InputSlot Cassette1
*%UIConstraints: *PageSize Monarch        *InputSlot Cassette2
*%UIConstraints: *PageSize Monarch        *InputSlot Cassette3
*%UIConstraints: *PageSize Monarch        *InputSlot Cassette4
*%UIConstraints: *PageSize Monarch        *Duplex DuplexS
*%UIConstraints: *PageSize Monarch        *Duplex DuplexT

*%UIConstraints: *PageRegion A6        *InputSlot Cassette1
*%UIConstraints: *PageRegion A6        *InputSlot Cassette2
*%UIConstraints: *PageRegion A6        *InputSlot Cassette3
*%UIConstraints: *PageRegion A6        *InputSlot Cassette4
*%UIConstraints: *PageRegion A6        *Duplex DuplexS
*%UIConstraints: *PageRegion A6        *Duplex DuplexT
*%UIConstraints: *PageRegion Comm10        *InputSlot Cassette1
*%UIConstraints: *PageRegion Comm10        *InputSlot Cassette2
*%UIConstraints: *PageRegion Comm10        *InputSlot Cassette3
*%UIConstraints: *PageRegion Comm10        *InputSlot Cassette4
*%UIConstraints: *PageRegion Comm10        *Duplex DuplexS
*%UIConstraints: *PageRegion Comm10        *Duplex DuplexT
*%UIConstraints: *PageRegion Monarch        *InputSlot Cassette1
*%UIConstraints: *PageRegion Monarch        *InputSlot Cassette2
*%UIConstraints: *PageRegion Monarch        *InputSlot Cassette3
*%UIConstraints: *PageRegion Monarch        *InputSlot Cassette4
*%UIConstraints: *PageRegion Monarch        *Duplex DuplexS
*%UIConstraints: *PageRegion Monarch        *Duplex DuplexT

*% paper size not work with Letter head
*UIConstraints: *PaperType LetterH   *PageSize A3
*UIConstraints: *PaperType LetterH   *PageSize A5
*%UIConstraints: *PaperType LetterH   *PageSize A6
*UIConstraints: *PaperType LetterH   *PageSize B4-JIS
*UIConstraints: *PaperType LetterH   *PageSize B5-JIS
*UIConstraints: *PaperType LetterH   *PageSize Ledger
*UIConstraints: *PaperType LetterH   *PageSize Legal
*%UIConstraints: *PaperType LetterH   *PageSize 13Legal
*UIConstraints: *PaperType LetterH   *PageSize Statement
*UIConstraints: *PaperType LetterH   *PageSize Computer
*UIConstraints: *PaperType LetterH   *PageSize Folio
*%UIConstraints: *PaperType LetterH   *PageSize Comm10
*%UIConstraints: *PaperType LetterH   *PageSize Monarch

*% tray1-4 and bypass not work with Lettr head
*UIConstraints: *PaperType LetterH   *InputSlot Cassette1
*UIConstraints: *PaperType LetterH   *InputSlot Cassette2
*UIConstraints: *PaperType LetterH   *InputSlot Cassette3
*UIConstraints: *PaperType LetterH   *InputSlot Cassette4
*UIConstraints: *PaperType LetterH   *InputSlot Manual




*LandscapeOrientation: Plus90
*VariablePaperSize: True

*% ==========================
*OpenUI *PageSize: PickOne
*OrderDependency: 30 AnySetup *PageSize
*DefaultPageSize: Letter
*PageSize A3/A3: "
       <</DeferredMediaSelection true /PageSize [842 1191] /ImagingBBox null>> setpagedevice"
*End
*PageSize A4/A4: "
       <</DeferredMediaSelection true /PageSize [595 842] /ImagingBBox null>> setpagedevice"
*End
*PageSize A5/A5: "
        <</DeferredMediaSelection true /PageSize [420 595] /ImagingBBox null>> setpagedevice"
*End
*%PageSize A6/A6: "
*%    <</DeferredMediaSelection true /PageSize [297 420] /ImagingBBox null>> setpagedevice"
*%End
*PageSize B4-JIS/B4: "
       <</DeferredMediaSelection true /PageSize [729 1032] /ImagingBBox null>> setpagedevice"
*End
*PageSize B5-JIS/B5: "
        <</DeferredMediaSelection true /PageSize [516 729] /ImagingBBox null>> setpagedevice"
*End
*PageSize Ledger/LEDGER: "
       <</DeferredMediaSelection true /PageSize [792 1224] /ImagingBBox null>> setpagedevice"
*End
*PageSize Legal/LEGAL: "
       <</DeferredMediaSelection true /PageSize [612 1008] /ImagingBBox null>> setpagedevice"
*End
*PageSize Letter/LETTER: "
        <</DeferredMediaSelection true /PageSize [612 792] /ImagingBBox null>> setpagedevice"
*End
*PageSize Statement/STATEMENT: "
        <</DeferredMediaSelection true /PageSize [396 612] /ImagingBBox null>> setpagedevice"
*End
*PageSize Computer/COMPUTER: "
    <</DeferredMediaSelection true /PageSize [729 1008] /ImagingBBox null>> setpagedevice"
*End
*PageSize Folio/FOLIO: "
       <</DeferredMediaSelection true /PageSize [595 935] /ImagingBBox null>> setpagedevice"
*End
*%PageSize Comm10/Env-#10: "
*%    <</DeferredMediaSelection true /PageSize [297 684] /ImagingBBox null>> setpagedevice"
*%End
*%PageSize Monarch/Env-Monarch Env:"
*%    <</DeferredMediaSelection true /PageSize [279 540] /ImagingBBox null>> setpagedevice"
*%End

*CloseUI: *PageSize


*OpenUI *PageRegion:  PickOne
*OrderDependency: 40 AnySetup *PageRegion
*DefaultPageRegion: Letter

*PageRegion A3/A3: "
        <</DeferredMediaSelection true /PageSize [842 1191] /ImagingBBox null>> setpagedevice"
*End
*PageRegion A4/A4: "
        <</DeferredMediaSelection true /PageSize [595 842] /ImagingBBox null>> setpagedevice"
*End
*PageRegion A5/A5: "
        <</DeferredMediaSelection true /PageSize [420 595] /ImagingBBox null>> setpagedevice"
*End
*%PageRegion A6/A6: "
*%    <</DeferredMediaSelection true /PageSize [297 420] /ImagingBBox null>> setpagedevice"
*%End
*PageRegion B4-JIS/B4: "
        <</DeferredMediaSelection true /PageSize [729 1032] /ImagingBBox null>> setpagedevice"
*End
*PageRegion B5-JIS/B5: "
        <</DeferredMediaSelection true /PageSize [516 729] /ImagingBBox null>> setpagedevice"
*End
*PageRegion Ledger/LEDGER: "
        <</DeferredMediaSelection true /PageSize [792 1224] /ImagingBBox null>> setpagedevice"
*End
*PageRegion Legal/LEGAL: "
        <</DeferredMediaSelection true /PageSize [612 1008] /ImagingBBox null>> setpagedevice"
*End
*PageRegion Letter/LETTER: "
        <</DeferredMediaSelection true /PageSize [612 792] /ImagingBBox null>> setpagedevice"
*End
*PageRegion Statement/STATEMENT: "
        <</DeferredMediaSelection true /PageSize [396 612] /ImagingBBox null>> setpagedevice"
*End
*PageRegion Computer/COMPUTER: "
    <</DeferredMediaSelection true /PageSize [729 1008] /ImagingBBox null>> setpagedevice"
*End
*PageRegion Folio/FOLIO: "
        <</DeferredMediaSelection true /PageSize [595 935] /ImagingBBox null>> setpagedevice"
*End
*%PageRegion Comm10/Env-#10 Env: "
*%    <</DeferredMediaSelection true /PageSize [297 684] /ImagingBBox null>> setpagedevice"
*%End
*%PageRegion Monarch/Env-Monarch: "
*%    <</DeferredMediaSelection true /PageSize [279 540] /ImagingBBox null>> setpagedevice"
*%End

*CloseUI: *PageRegion


*DefaultImageableArea: Letter
*ImageableArea A3/A3:"12.00 12.00 830.00 1179.00 "
*ImageableArea A4/A4: "12.00 12.00 583.00 830.00 "
*ImageableArea A5/A5: "12.00 12.00 408.00 583.00 "
*%ImageableArea A6/A6:  "12.00 12.00 285.00 408.00 "
*ImageableArea B4-JIS/B4: "12.00 12.00 717.00 1020.00"
*ImageableArea B5-JIS/B5: "12.00 12.00 504.00 717.00 "
*ImageableArea Ledger/LEDGER: "12.00 12.00 780.00 1212.00 "
*ImageableArea Legal/LEGAL: "12.00 12.00 600.00 996.00 "
*ImageableArea Letter/LETTER: "12.00 12.00 600.00 780.00 "
*ImageableArea Statement/STATEMENT: "12.00 12.00 384.00 600.00 "
*ImageableArea Computer/COMPUTER: "12.00 12.00 716.00 996.00 "
*ImageableArea Folio/FOLIO: "12.00 12.00 583.00 923.00"
*%ImageableArea Comm10/Env-#10: "12.00 12.00 285.00 672.00 "
*%ImageableArea Monarch/Env-Monarch: "12.00 12.00 267.00 528.00 "

*DefaultPaperDimension: Letter
*PaperDimension A3/A3: "842 1191"
*PaperDimension A4/A4: "595 842"
*PaperDimension A5/A5: "420 595"
*%PaperDimension A6/A6: "297 420"
*PaperDimension B4-JIS/B4: "729 1032"
*PaperDimension B5-JIS/B5: "516 729"
*PaperDimension Ledger/LEDGER: "792 1224"
*PaperDimension Legal/LEGAL: "612 1008"
*PaperDimension Letter/LETTER: "612 792"
*PaperDimension Statement/STATEMENT: "396 612"
*PaperDimension Folio/FOLIO: "595 935"
*PaperDimension Computer/COMPUTER: "729 1008"
*%PaperDimension Comm10/Env-#10: "297 684"
*%PaperDimension Monarch/Env-Monarch: "279 540"
*RequiresPageRegion All: True

*JCLBegin: "<1B>%-12345X@PJL JOB<0A>@PJL SET RESOLUTION = 600<0A>"
*JCLToPSInterpreter: "@PJL ENTER LANGUAGE = POSTSCRIPT <0A>"
*JCLEnd: ""

*%JCLOpenUI *JCLEconomode/EconoMode: Boolean
*%DefaultJCLEconomode: PrinterDefault
*%OrderDependency: 10 JCLSetup  *JCLEconomode
*%JCLEconomode on/On: "@PJL SET ECONOMODE = ON<0A>"
*%JCLEconomode off/Off: "@PJL SET ECONOMODE = OFF<0A>"
*%JCLCloseUI: *JCLEconomode



*OpenUI *InputSlot: PickOne
*OrderDependency: 20 AnySetup *InputSlot
*DefaultInputSlot: Auto
*InputSlot Auto/Auto Select: "
    <</DeferredMediaSelection true /MediaPosition 0>> setpagedevice"
*End
*InputSlot Manual/Stack Feed Bypass: "
    <</DeferredMediaSelection true /MediaPosition 1>> setpagedevice"
*End
*InputSlot Cassette1/Cassette 1: "
    <</DeferredMediaSelection true /MediaPosition 2>> setpagedevice"
*End
*InputSlot Cassette2/Cassette 2: "
    <</DeferredMediaSelection true /MediaPosition 3>> setpagedevice"
*End
*InputSlot Cassette3/Cassette 3: "
        <</DeferredMediaSelection true /MediaPosition 4>> setpagedevice"
*End
*InputSlot Cassette4/Cassette 4: "
        <</DeferredMediaSelection true /MediaPosition 5>> setpagedevice"
*End
*InputSlot LCF/Large Capacity Feeder: "
        <</DeferredMediaSelection true /MediaPosition 6>> setpagedevice"
*End
*CloseUI: *InputSlot

*OpenUI *Offset/Offset Stack: PickOne
*DefaultOffset: Off
*Offset Off/Off: "
        <</ShiftMode 0>> setpagedevice "
*Offset On/On: "
        <</ShiftMode 1>> setpagedevice "
*CloseUI: *Offset

*OpenUI *Option6/Toner Saving: PickOne
*DefaultOption6: Off
*Option6 Off/Off: "
        <</TonerSave 0>> setpagedevice "
*End
*Option6 On/On: "
        <</TonerSave 1>> setpagedevice "
*End
*CloseUI: *Option6


*OpenUI *OutputBin/Paper Destination: PickOne
*%OrderDependency: 30 AnySetup *OutputBin
*%DefaultOutputBin: Inner/Finisher Tray2
*DefaultOutputBin: Inner/Standard Output Tray
*OutputBin	Inner/Standard Output Tray:" 
     <</OutSlot 0>> setpagedevice"
*End
*OutputBin	Upper/Job Separator Upper Tray:" 
     <</OutSlot 1>> setpagedevice"
*End
*OutputBin	Lower/Job Separator Lower Tray:" 
     <</OutSlot 2>> setpagedevice"
*End
*OutputBin	T1/Finisher Tray1:" 
     <</OutSlot 4>> setpagedevice"
*End
*OutputBin	T2/Finisher Tray2:" 
     <</OutSlot 5>> setpagedevice"
*End
*CloseUI: *OutputBin


*OpenUI *Duplex/Duplex: PickOne
*DefaultDuplex: None
*Duplex None/Off: "
        <</Duplex false>> setpagedevice"
*End
*Duplex DuplexS/Booklet: "
        <</Duplex true /Tumble false>> setpagedevice"
*End
*Duplex DuplexT/Tablet: "
        <</Duplex true /Tumble true>> setpagedevice"
*End
*CloseUI: *Duplex

*OpenUI *PaperType/Media Type: PickOne
*DefaultPaperType: Plain
*PaperType Plain/Plain Paper: "
        <</PaperType 0>> setpagedevice"
*End
*PaperType Envelopes/Envelopes: "
        <</PaperType 1>> setpagedevice"
*End
*PaperType Transparencies/Transparencies: "
        <</PaperType 2>> setpagedevice"
*End
*PaperType Labels/Labels: "
        <</PaperType 3>> setpagedevice"
*End
*PaperType Cardstocks/Cardstocks: "
        <</PaperType 4>> setpagedevice"
*End
*PaperType LetterH/Letter Head: "
        <</PaperType 5>> setpagedevice"
*End
*CloseUI: *PaperType

*OpenUI *Option7/Edge Smoothing: PickOne
*DefaultOption7: On
*Option7 Off/Off: "
        <</EET 0>> setpagedevice"
*End
*Option7 On/On: "
        <</EET 1>> setpagedevice"
*End
*CloseUI: *Option7

*OpenUI *Option8/Collate: PickOne
*DefaultOption8: True
*Option8 True/On (turn off in application): "
        <</Collate true>> setpagedevice"
*End
*Option8 False/Off: "
        <</Collate false>> setpagedevice"
*End
*CloseUI: *Option8

*OpenUI *Resolution: PickOne
*DefaultResolution: 600dpi
*Resolution 600dpi/600: "
        <</HWResolution [600 600]>> setpagedevice"
*End
*Resolution 300dpi/300: "
        <</HWResolution [300 300]>> setpagedevice"
*End
*CloseUI: *Resolution


*MaxMediaWidth: "1224"
*MaxMediaHeight: "1224"
*HWMargins: 16 16 16 16



*DefaultTransfer: Null
*Transfer Null: "{ }"
*Transfer Null.Inverse: "{ 1 exch sub }"

*DefaultFont: Courier
*Font Wingdings-Regular: Standard "(001.002)" Standard ROM
*Font Albertus-Medium: Standard "(001.002)" Standard ROM
*Font AvantGarde-Book: Standard "(001.006)" Standard ROM
*Font AvantGarde-BookOblique: Standard "(001.006)" Standard ROM
*Font AvantGarde-Demi: Standard "(001.007)" Standard ROM
*Font AvantGarde-DemiOblique: Standard "(001.007)" Standard ROM
*Font Bookman-Demi: Standard "(001.003)" Standard ROM
*Font Bookman-DemiItalic: Standard "(001.003)" Standard ROM
*Font Bookman-Light: Standard "(001.003)" Standard ROM
*Font Bookman-LightItalic: Standard "(001.003)" Standard ROM
*Font Courier: Standard "(002.004)" Standard ROM
*Font Courier-Bold: Standard "(002.004)" Standard ROM
*Font Courier-BoldOblique: Standard "(002.004)" Standard ROM
*Font Courier-Oblique: Standard "(002.004)" Standard ROM
*Font Helvetica: Standard "(001.006)" Standard ROM
*Font Helvetica-Bold: Standard "(001.007)" Standard ROM
*Font Helvetica-BoldOblique: Standard "(001.007)" Standard ROM
*Font Helvetica-Narrow: Standard "(001.006)" Standard ROM
*Font Helvetica-Narrow-Bold: Standard "(001.007)" Standard ROM
*Font Helvetica-Narrow-BoldOblique: Standard "(001.007)" Standard ROM
*Font Helvetica-Narrow-Oblique: Standard "(001.006)" Standard ROM
*Font Helvetica-Oblique: Standard "(001.006)" Standard ROM
*Font NewCenturySchlbk-Bold: Standard "(001.009)" Standard ROM
*Font NewCenturySchlbk-BoldItalic: Standard "(001.007)" Standard ROM
*Font NewCenturySchlbk-Italic: Standard "(001.006)" Standard ROM
*Font NewCenturySchlbk-Roman: Standard "(001.007)" Standard ROM
*Font Palatino-Bold: Standard "(001.005)" Standard ROM
*Font Palatino-BoldItalic: Standard "(001.005)" Standard ROM
*Font Palatino-Italic: Standard "(001.005)" Standard ROM
*Font Palatino-Roman: Standard "(001.005)" Standard ROM
*Font Symbol: Special "(001.007)" Special ROM
*Font Times-Bold: Standard "(001.007)" Standard ROM
*Font Times-BoldItalic: Standard "(001.009)" Standard ROM
*Font Times-Italic: Standard "(001.007)" Standard ROM
*Font Times-Roman: Standard "(001.007)" Standard ROM
*Font ZapfChancery-MediumItalic: Standard "(001.007)" Standard ROM
*Font ZapfDingbats: Special "(001.004)" Special ROM
*Font Albertus-ExtraBold: Standard "(001.002)" Standard ROM
*Font AntiqueOlive: Standard "(001.003)" Standard ROM
*Font AntiqueOlive-Italic: Standard "(001.003)" Standard ROM
*Font AntiqueOlive-Bold: Standard "(001.003)" Standard ROM
*Font Clarendon-Condensed-Bold: Standard "(001.002)" Standard ROM
*Font Marigold: Standard "(001.002)" Standard ROM
*Font Coronet: Standard "(001.007)" Standard ROM
*Font CourierHP-Italic: Standard "(001.006)" Standard ROM
*Font CourierHP-BoldItalic: Standard "(001.006)" Standard ROM
*Font CourierHP: Standard "(001.006)" Standard ROM
*Font CourierHP-Bold: Standard "(001.006)" Standard ROM
*Font Garamond-Antiqua: Standard "(001.005)" Standard ROM
*Font Garamond-Halbfett: Standard "(001.005)" Standard ROM
*Font Garamond-Kursiv: Standard "(001.005)" Standard ROM
*Font Garamond-KursivHalbfett: Standard "(001.005)" Standard ROM
*Font LetterGothic: Standard "(001.007)" Standard ROM
*Font LetterGothic-Italic: Standard "(001.007)" Standard ROM
*Font LetterGothic-Bold: Standard "(001.007)" Standard ROM
*Font CGOmega: Standard"(001.009)" Standard ROM
*Font CGOmega-Italic: Standard"(001.009)" Standard ROM
*Font CGOmega-Bold: Standard"(001.009)" Standard ROM
*Font CGOmega-BoldItalic: Standard"(001.009)" Standard ROM
*Font CGTimes: Standard "(001.009)" Standard ROM
*Font CGTimes-Italic: Standard "(001.009)" Standard ROM
*Font CGTimes-Bold: Standard "(001.009)" Standard ROM
*Font CGTimes-BoldItalic: Standard "(001.009)" Standard ROM
*Font Univers-Medium: Standard "(001.008)" Standard ROM
*Font Univers-MediumItalic: Standard "(001.008)" Standard ROM
*Font Univers-Bold: Standard "(001.008)" Standard ROM

---

### Post by andrew.george.hammond on 2006-07-05
You'll need the following ppd file. Copy it into e-studio16_20_25.ppd

Trying again with retardo smilies disabled. You then add a printer and use this as the driver. I haven't got mine working yet, but I understand this is part of the process.

-------- snip ---
*PPD-Adobe: "4.3"

*% =======================================================
*%  Printer Description file
*%    for "TOSHIBA e-STUDIO16/20/25 Series" for MAC PPD file
*%    Version 1.18
*%    CreationDate: 2000/05/10
*%    Modified:     2001/04/25
*%
*%    COPYRIGHT (C) 2000-2001 TOSHIBA TEC Corp.
*%    COPYRIGHT (C) 2000-2001 DESTINY Ltd.
*%    All rights reserved.
*% =======================================================

*FormatVersion: "4.3"
*FileVersion: "1.2.0"
*LanguageVersion: English
*LanguageEncoding: ISOLatin1
*Manufacturer: "Toshiba"
*PCFileName: "TSBeST16.ppd"
*Product: "(TOSHIBA e-STUDIO16/20/25)"
*PSVersion: "(2014.108) 1"
*ModelName: "TOSHIBA e-STUDIO16/20/25"
*NickName: "TOSHIBA e-STUDIO16/20/25"
*ShortNickName: "TOSHIBA e-STUDIO16/20/25"

*LanguageLevel: "2"
*Protocols: PJL
*ColorDevice: False
*DefaultColorSpace: Gray
*TTRasterizer: Type42
*FileSystem: False
*Throughput: "17"

*OpenGroup: InstallableOptions

*OpenUI *Option1/Duplex Unit: Boolean
*DefaultOption1: False
*Option1 True/Installed: ""
*Option1 False/Not Installed: ""
*CloseUI: *Option1

*OpenUI *Option21/Cassette2: Boolean
*DefaultOption21: False
*Option21 True/Installed: " "
*Option21 False/Not Installed: ""
*CloseUI: *Option21

*OpenUI *Option20/Cassette3: Boolean
*DefaultOption20: False
*Option20 True/Installed: " "
*Option20 False/Not Installed: ""
*CloseUI: *Option20

*OpenUI *Option24/Cassette4: Boolean
*DefaultOption24: False
*Option24 True/Installed: " "
*Option24 False/Not Installed: ""
*CloseUI: *Option24

*OpenUI *Option25/Large Capacity Feeder: Boolean
*DefaultOption25: False
*Option25 True/Installed: " "
*Option25 False/Not Installed: ""
*CloseUI: *Option25

*OpenUI *Option22/Stack Feed Bypass: Boolean
*DefaultOption22: False
*Option22 True/Installed: " "
*Option22 False/Not Installed: ""
*CloseUI: *Option22

*OpenUI *Option23/Others: PickOne
*DefaultOption23: None
*Option23 None/Not Installed: ""
*Option23 Finisher/Finisher: ""
*Option23 Offset/Offset Stacker: ""
*Option23 Job/Job Separator: ""
*CloseUI: *Option23

*CloseGroup: InstallableOptions




*% LCF tray can not exist when Tray2 is not installed
*UIConstraints: *Option21 False	*Option25 True

*% Tray3 tray can not exist when Tray2 is not installed
*% Tray4 tray can not exist when Tray2 or Tray3 is not installed
*UIConstraints: *Option21 False	*Option20 True
*UIConstraints: *Option21 False	*Option24 True
*UIConstraints: *Option20 False	*Option24 True

*UIConstraints: *Option24 False *InputSlot Cassette4
*UIConstraints: *Option20 False *InputSlot Cassette3
*UIConstraints: *Option21 False *InputSlot Cassette2
*UIConstraints: *InputSlot Cassette4 *Option24 False
*UIConstraints: *InputSlot Cassette3 *Option20 False
*UIConstraints: *InputSlot Cassette2 *Option21 False

*% Tray4 and Tray3 tray can not exist when LCF is installed
*UIConstraints: *Option20 True	*Option25 True
*UIConstraints: *Option24 True	*Option25 True

*%Job Trays is disabled when Job Separator is not installed
*UIConstraints: *Option23 None *OutputBin Lower
*UIConstraints: *Option23 None *OutputBin Upper
*UIConstraints: *Option23 None *OutputBin T1
*UIConstraints: *Option23 None *OutputBin T2

*UIConstraints: *Option23 Offset *OutputBin Lower
*UIConstraints: *Option23 Offset *OutputBin Upper
*UIConstraints: *Option23 Offset *OutputBin T1
*UIConstraints: *Option23 Offset *OutputBin T2

*UIConstraints: *Option23 Job *OutputBin T1
*UIConstraints: *Option23 Job *OutputBin T2
*UIConstraints: *Option23 Finisher *OutputBin Lower
*UIConstraints: *Option23 Finisher *OutputBin Upper

*%Finisher Trays is disabled when Finisher is not installed
*UIConstraints: *Option23 Finisher *OutputBin Lower
*UIConstraints: *Option23 Finisher *OutputBin Upper

*%Offset is disabled when Offset is not installed
*UIConstraints: *Option23 None *Offset On
*UIConstraints: *Option23 Job *Offset On

*% duplex installed or not installed
*UIConstraints:  *Option1 False *Duplex DuplexS
*UIConstraints:  *Option1 False *Duplex DuplexT

*% Paper Size not work with Offset
*%UIConstraints: *Offset On	*PageSize A6
*%UIConstraints: *Offset On	*PageSize Comm10
*%UIConstraints: *Offset On	*PageSize Monarch
*UIConstraints: *Offset On	*PageSize A5
*UIConstraints: *Offset On	*PageSize Statement

*% Edge Smoothing is disable when Toner Saver is On
*UIConstraints: *Option6 On  *Option7 On

*% Paper Type not work with Job Upper
*UIConstraints: *OutputBin	Upper		*PaperType Envelopes
*UIConstraints: *OutputBin	Upper		*PaperType Transparencies
*UIConstraints: *OutputBin	Upper		*PaperType Labels
*UIConstraints: *OutputBin	Upper		*PaperType Cardstocks

*% Paper Type not work with Offset
*UIConstraints: *Offset On	*PaperType Envelopes
*UIConstraints: *Offset On	*PaperType Transparencies
*UIConstraints: *Offset On	*PaperType Labels
*UIConstraints: *Offset On	*PaperType Cardstocks

*% Paper Type not work with Duplex
*UIConstraints: *Duplex DuplexS	*PaperType Envelopes
*UIConstraints: *Duplex DuplexS	*PaperType Transparencies
*UIConstraints: *Duplex DuplexS	*PaperType Labels
*UIConstraints: *Duplex DuplexS	*PaperType Cardstocks
*UIConstraints: *Duplex DuplexT	*PaperType Envelopes
*UIConstraints: *Duplex DuplexT	*PaperType Transparencies
*UIConstraints: *Duplex DuplexT	*PaperType Labels
*UIConstraints: *Duplex DuplexT	*PaperType Cardstocks

*% Paper Type not work with tray1-4 & LCF
*UIConstraints: *InputSlot Cassette1	*PaperType Envelopes
*UIConstraints: *InputSlot Cassette1	*PaperType Transparencies
*UIConstraints: *InputSlot Cassette1	*PaperType Labels
*UIConstraints: *InputSlot Cassette1	*PaperType Cardstocks
*UIConstraints: *InputSlot Cassette2	*PaperType Envelopes
*UIConstraints: *InputSlot Cassette2	*PaperType Transparencies
*UIConstraints: *InputSlot Cassette2	*PaperType Labels
*UIConstraints: *InputSlot Cassette2	*PaperType Cardstocks
*UIConstraints: *InputSlot Cassette3	*PaperType Envelopes
*UIConstraints: *InputSlot Cassette3	*PaperType Transparencies
*UIConstraints: *InputSlot Cassette3	*PaperType Labels
*UIConstraints: *InputSlot Cassette3	*PaperType Cardstocks
*UIConstraints: *InputSlot Cassette4	*PaperType Envelopes
*UIConstraints: *InputSlot Cassette4	*PaperType Transparencies
*UIConstraints: *InputSlot Cassette4	*PaperType Labels
*UIConstraints: *InputSlot Cassette4	*PaperType Cardstocks
*UIConstraints: *InputSlot LCF		*PaperType Envelopes
*UIConstraints: *InputSlot LCF		*PaperType Transparencies
*UIConstraints: *InputSlot LCF		*PaperType Labels
*UIConstraints: *InputSlot LCF		*PaperType Cardstocks

*UIConstraints: *InputSlot Auto	*PaperType Cardstocks
*UIConstraints: *InputSlot Auto	*PaperType Envelopes
*UIConstraints: *InputSlot Auto	*PaperType Transparencies
*UIConstraints: *InputSlot Auto	*PaperType Labels
*UIConstraints: *InputSlot Auto	*PaperType Cardstocks

*% Paper Type is disabled when Bypass Tray is not installed
*UIConstraints: *Option22 False	*PaperType Envelopes
*UIConstraints: *Option22 False	*PaperType Transparencies
*UIConstraints: *Option22 False	*PaperType Labels
*UIConstraints: *Option22 False	*PaperType Cardstocks

*% Bypass Tray is disabled when Bypass Tray is not installed
*UIConstraints: *Option22 False        *InputSlot Manual
*%UIConstraints: *Option22 False        *PageSize A6
*%UIConstraints: *Option22 False        *PageSize Comm10
*%UIConstraints: *Option22 False        *PageSize Monarch

*% LCF Tray is disabled when LCF is not installed
*UIConstraints: *Option25 False	*InputSlot LCF

*% LCF don't support lots of paper size.
*UIConstraints: *InputSlot LCF	*PageSize A3
*UIConstraints: *InputSlot LCF	*PageSize A5
*%UIConstraints: *InputSlot LCF	 *PageSize A6
*UIConstraints: *InputSlot LCF	*PageSize B4-JIS
*UIConstraints: *InputSlot LCF	*PageSize B5-JIS
*UIConstraints: *InputSlot LCF	*PageSize Ledger
*UIConstraints: *InputSlot LCF	*PageSize Legal
*%UIConstraints: *InputSlot LCF	 *PageSize 13Legal
*UIConstraints: *InputSlot LCF	*PageSize Statement
*UIConstraints: *InputSlot LCF	*PageSize Computer
*UIConstraints: *InputSlot LCF	*PageSize Folio
*%UIConstraints: *InputSlot LCF	 *PageSize Monarch
*%UIConstraints: *InputSlot LCF	 *PageSize Comm10

*UIConstraints:	*PageSize A3		 *InputSlot LCF
*UIConstraints:	*PageSize A5		 *InputSlot LCF
*%UIConstraints:	*PageSize A6		 *InputSlot LCF
*UIConstraints:	*PageSize B4-JIS	 *InputSlot LCF
*UIConstraints:	*PageSize B5-JIS	 *InputSlot LCF
*UIConstraints:	*PageSize Ledger	 *InputSlot LCF
*UIConstraints:	*PageSize Legal		 *InputSlot LCF
*%UIConstraints:	*PageSize 13Legal	 *InputSlot LCF
*UIConstraints:	*PageSize Statement	 *InputSlot LCF
*UIConstraints:	*PageSize Computer	 *InputSlot LCF
*UIConstraints:	*PageSize Folio		 *InputSlot LCF
*%UIConstraints:	*PageSize Monarch	 *InputSlot LCF
*%UIConstraints:	*PageSize Comm10	 *InputSlot LCF

*% paper size not work with tray1-4 and Duplex
*%UIConstraints: *PageSize A6        *InputSlot Cassette1
*%UIConstraints: *PageSize A6        *InputSlot Cassette2
*%UIConstraints: *PageSize A6        *InputSlot Cassette3
*%UIConstraints: *PageSize A6        *InputSlot Cassette4
*%UIConstraints: *PageSize A6        *Duplex DuplexS
*%UIConstraints: *PageSize A6        *Duplex DuplexT
*%UIConstraints: *PageSize Comm10        *InputSlot Cassette1
*%UIConstraints: *PageSize Comm10        *InputSlot Cassette2
*%UIConstraints: *PageSize Comm10        *InputSlot Cassette3
*%UIConstraints: *PageSize Comm10        *InputSlot Cassette4
*%UIConstraints: *PageSize Comm10        *Duplex DuplexS
*%UIConstraints: *PageSize Comm10        *Duplex DuplexT
*%UIConstraints: *PageSize Monarch        *InputSlot Cassette1
*%UIConstraints: *PageSize Monarch        *InputSlot Cassette2
*%UIConstraints: *PageSize Monarch        *InputSlot Cassette3
*%UIConstraints: *PageSize Monarch        *InputSlot Cassette4
*%UIConstraints: *PageSize Monarch        *Duplex DuplexS
*%UIConstraints: *PageSize Monarch        *Duplex DuplexT

*%UIConstraints: *PageRegion A6        *InputSlot Cassette1
*%UIConstraints: *PageRegion A6        *InputSlot Cassette2
*%UIConstraints: *PageRegion A6        *InputSlot Cassette3
*%UIConstraints: *PageRegion A6        *InputSlot Cassette4
*%UIConstraints: *PageRegion A6        *Duplex DuplexS
*%UIConstraints: *PageRegion A6        *Duplex DuplexT
*%UIConstraints: *PageRegion Comm10        *InputSlot Cassette1
*%UIConstraints: *PageRegion Comm10        *InputSlot Cassette2
*%UIConstraints: *PageRegion Comm10        *InputSlot Cassette3
*%UIConstraints: *PageRegion Comm10        *InputSlot Cassette4
*%UIConstraints: *PageRegion Comm10        *Duplex DuplexS
*%UIConstraints: *PageRegion Comm10        *Duplex DuplexT
*%UIConstraints: *PageRegion Monarch        *InputSlot Cassette1
*%UIConstraints: *PageRegion Monarch        *InputSlot Cassette2
*%UIConstraints: *PageRegion Monarch        *InputSlot Cassette3
*%UIConstraints: *PageRegion Monarch        *InputSlot Cassette4
*%UIConstraints: *PageRegion Monarch        *Duplex DuplexS
*%UIConstraints: *PageRegion Monarch        *Duplex DuplexT

*% paper size not work with Letter head
*UIConstraints: *PaperType LetterH   *PageSize A3
*UIConstraints: *PaperType LetterH   *PageSize A5
*%UIConstraints: *PaperType LetterH   *PageSize A6
*UIConstraints: *PaperType LetterH   *PageSize B4-JIS
*UIConstraints: *PaperType LetterH   *PageSize B5-JIS
*UIConstraints: *PaperType LetterH   *PageSize Ledger
*UIConstraints: *PaperType LetterH   *PageSize Legal
*%UIConstraints: *PaperType LetterH   *PageSize 13Legal
*UIConstraints: *PaperType LetterH   *PageSize Statement
*UIConstraints: *PaperType LetterH   *PageSize Computer
*UIConstraints: *PaperType LetterH   *PageSize Folio
*%UIConstraints: *PaperType LetterH   *PageSize Comm10
*%UIConstraints: *PaperType LetterH   *PageSize Monarch

*% tray1-4 and bypass not work with Lettr head
*UIConstraints: *PaperType LetterH   *InputSlot Cassette1
*UIConstraints: *PaperType LetterH   *InputSlot Cassette2
*UIConstraints: *PaperType LetterH   *InputSlot Cassette3
*UIConstraints: *PaperType LetterH   *InputSlot Cassette4
*UIConstraints: *PaperType LetterH   *InputSlot Manual




*LandscapeOrientation: Plus90
*VariablePaperSize: True

*% ==========================
*OpenUI *PageSize: PickOne
*OrderDependency: 30 AnySetup *PageSize
*DefaultPageSize: Letter
*PageSize A3/A3: "
       <</DeferredMediaSelection true /PageSize [842 1191] /ImagingBBox null>> setpagedevice"
*End
*PageSize A4/A4: "
       <</DeferredMediaSelection true /PageSize [595 842] /ImagingBBox null>> setpagedevice"
*End
*PageSize A5/A5: "
        <</DeferredMediaSelection true /PageSize [420 595] /ImagingBBox null>> setpagedevice"
*End
*%PageSize A6/A6: "
*%    <</DeferredMediaSelection true /PageSize [297 420] /ImagingBBox null>> setpagedevice"
*%End
*PageSize B4-JIS/B4: "
       <</DeferredMediaSelection true /PageSize [729 1032] /ImagingBBox null>> setpagedevice"
*End
*PageSize B5-JIS/B5: "
        <</DeferredMediaSelection true /PageSize [516 729] /ImagingBBox null>> setpagedevice"
*End
*PageSize Ledger/LEDGER: "
       <</DeferredMediaSelection true /PageSize [792 1224] /ImagingBBox null>> setpagedevice"
*End
*PageSize Legal/LEGAL: "
       <</DeferredMediaSelection true /PageSize [612 1008] /ImagingBBox null>> setpagedevice"
*End
*PageSize Letter/LETTER: "
        <</DeferredMediaSelection true /PageSize [612 792] /ImagingBBox null>> setpagedevice"
*End
*PageSize Statement/STATEMENT: "
        <</DeferredMediaSelection true /PageSize [396 612] /ImagingBBox null>> setpagedevice"
*End
*PageSize Computer/COMPUTER: "
    <</DeferredMediaSelection true /PageSize [729 1008] /ImagingBBox null>> setpagedevice"
*End
*PageSize Folio/FOLIO: "
       <</DeferredMediaSelection true /PageSize [595 935] /ImagingBBox null>> setpagedevice"
*End
*%PageSize Comm10/Env-#10: "
*%    <</DeferredMediaSelection true /PageSize [297 684] /ImagingBBox null>> setpagedevice"
*%End
*%PageSize Monarch/Env-Monarch Env:"
*%    <</DeferredMediaSelection true /PageSize [279 540] /ImagingBBox null>> setpagedevice"
*%End

*CloseUI: *PageSize


*OpenUI *PageRegion:  PickOne
*OrderDependency: 40 AnySetup *PageRegion
*DefaultPageRegion: Letter

*PageRegion A3/A3: "
        <</DeferredMediaSelection true /PageSize [842 1191] /ImagingBBox null>> setpagedevice"
*End
*PageRegion A4/A4: "
        <</DeferredMediaSelection true /PageSize [595 842] /ImagingBBox null>> setpagedevice"
*End
*PageRegion A5/A5: "
        <</DeferredMediaSelection true /PageSize [420 595] /ImagingBBox null>> setpagedevice"
*End
*%PageRegion A6/A6: "
*%    <</DeferredMediaSelection true /PageSize [297 420] /ImagingBBox null>> setpagedevice"
*%End
*PageRegion B4-JIS/B4: "
        <</DeferredMediaSelection true /PageSize [729 1032] /ImagingBBox null>> setpagedevice"
*End
*PageRegion B5-JIS/B5: "
        <</DeferredMediaSelection true /PageSize [516 729] /ImagingBBox null>> setpagedevice"
*End
*PageRegion Ledger/LEDGER: "
        <</DeferredMediaSelection true /PageSize [792 1224] /ImagingBBox null>> setpagedevice"
*End
*PageRegion Legal/LEGAL: "
        <</DeferredMediaSelection true /PageSize [612 1008] /ImagingBBox null>> setpagedevice"
*End
*PageRegion Letter/LETTER: "
        <</DeferredMediaSelection true /PageSize [612 792] /ImagingBBox null>> setpagedevice"
*End
*PageRegion Statement/STATEMENT: "
        <</DeferredMediaSelection true /PageSize [396 612] /ImagingBBox null>> setpagedevice"
*End
*PageRegion Computer/COMPUTER: "
    <</DeferredMediaSelection true /PageSize [729 1008] /ImagingBBox null>> setpagedevice"
*End
*PageRegion Folio/FOLIO: "
        <</DeferredMediaSelection true /PageSize [595 935] /ImagingBBox null>> setpagedevice"
*End
*%PageRegion Comm10/Env-#10 Env: "
*%    <</DeferredMediaSelection true /PageSize [297 684] /ImagingBBox null>> setpagedevice"
*%End
*%PageRegion Monarch/Env-Monarch: "
*%    <</DeferredMediaSelection true /PageSize [279 540] /ImagingBBox null>> setpagedevice"
*%End

*CloseUI: *PageRegion


*DefaultImageableArea: Letter
*ImageableArea A3/A3:"12.00 12.00 830.00 1179.00 "
*ImageableArea A4/A4: "12.00 12.00 583.00 830.00 "
*ImageableArea A5/A5: "12.00 12.00 408.00 583.00 "
*%ImageableArea A6/A6:  "12.00 12.00 285.00 408.00 "
*ImageableArea B4-JIS/B4: "12.00 12.00 717.00 1020.00"
*ImageableArea B5-JIS/B5: "12.00 12.00 504.00 717.00 "
*ImageableArea Ledger/LEDGER: "12.00 12.00 780.00 1212.00 "
*ImageableArea Legal/LEGAL: "12.00 12.00 600.00 996.00 "
*ImageableArea Letter/LETTER: "12.00 12.00 600.00 780.00 "
*ImageableArea Statement/STATEMENT: "12.00 12.00 384.00 600.00 "
*ImageableArea Computer/COMPUTER: "12.00 12.00 716.00 996.00 "
*ImageableArea Folio/FOLIO: "12.00 12.00 583.00 923.00"
*%ImageableArea Comm10/Env-#10: "12.00 12.00 285.00 672.00 "
*%ImageableArea Monarch/Env-Monarch: "12.00 12.00 267.00 528.00 "

*DefaultPaperDimension: Letter
*PaperDimension A3/A3: "842 1191"
*PaperDimension A4/A4: "595 842"
*PaperDimension A5/A5: "420 595"
*%PaperDimension A6/A6: "297 420"
*PaperDimension B4-JIS/B4: "729 1032"
*PaperDimension B5-JIS/B5: "516 729"
*PaperDimension Ledger/LEDGER: "792 1224"
*PaperDimension Legal/LEGAL: "612 1008"
*PaperDimension Letter/LETTER: "612 792"
*PaperDimension Statement/STATEMENT: "396 612"
*PaperDimension Folio/FOLIO: "595 935"
*PaperDimension Computer/COMPUTER: "729 1008"
*%PaperDimension Comm10/Env-#10: "297 684"
*%PaperDimension Monarch/Env-Monarch: "279 540"
*RequiresPageRegion All: True

*JCLBegin: "<1B>%-12345X@PJL JOB<0A>@PJL SET RESOLUTION = 600<0A>"
*JCLToPSInterpreter: "@PJL ENTER LANGUAGE = POSTSCRIPT <0A>"
*JCLEnd: ""

*%JCLOpenUI *JCLEconomode/EconoMode: Boolean
*%DefaultJCLEconomode: PrinterDefault
*%OrderDependency: 10 JCLSetup  *JCLEconomode
*%JCLEconomode on/On: "@PJL SET ECONOMODE = ON<0A>"
*%JCLEconomode off/Off: "@PJL SET ECONOMODE = OFF<0A>"
*%JCLCloseUI: *JCLEconomode



*OpenUI *InputSlot: PickOne
*OrderDependency: 20 AnySetup *InputSlot
*DefaultInputSlot: Auto
*InputSlot Auto/Auto Select: "
    <</DeferredMediaSelection true /MediaPosition 0>> setpagedevice"
*End
*InputSlot Manual/Stack Feed Bypass: "
    <</DeferredMediaSelection true /MediaPosition 1>> setpagedevice"
*End
*InputSlot Cassette1/Cassette 1: "
    <</DeferredMediaSelection true /MediaPosition 2>> setpagedevice"
*End
*InputSlot Cassette2/Cassette 2: "
    <</DeferredMediaSelection true /MediaPosition 3>> setpagedevice"
*End
*InputSlot Cassette3/Cassette 3: "
        <</DeferredMediaSelection true /MediaPosition 4>> setpagedevice"
*End
*InputSlot Cassette4/Cassette 4: "
        <</DeferredMediaSelection true /MediaPosition 5>> setpagedevice"
*End
*InputSlot LCF/Large Capacity Feeder: "
        <</DeferredMediaSelection true /MediaPosition 6>> setpagedevice"
*End
*CloseUI: *InputSlot

*OpenUI *Offset/Offset Stack: PickOne
*DefaultOffset: Off
*Offset Off/Off: "
        <</ShiftMode 0>> setpagedevice "
*Offset On/On: "
        <</ShiftMode 1>> setpagedevice "
*CloseUI: *Offset

*OpenUI *Option6/Toner Saving: PickOne
*DefaultOption6: Off
*Option6 Off/Off: "
        <</TonerSave 0>> setpagedevice "
*End
*Option6 On/On: "
        <</TonerSave 1>> setpagedevice "
*End
*CloseUI: *Option6


*OpenUI *OutputBin/Paper Destination: PickOne
*%OrderDependency: 30 AnySetup *OutputBin
*%DefaultOutputBin: Inner/Finisher Tray2
*DefaultOutputBin: Inner/Standard Output Tray
*OutputBin	Inner/Standard Output Tray:" 
     <</OutSlot 0>> setpagedevice"
*End
*OutputBin	Upper/Job Separator Upper Tray:" 
     <</OutSlot 1>> setpagedevice"
*End
*OutputBin	Lower/Job Separator Lower Tray:" 
     <</OutSlot 2>> setpagedevice"
*End
*OutputBin	T1/Finisher Tray1:" 
     <</OutSlot 4>> setpagedevice"
*End
*OutputBin	T2/Finisher Tray2:" 
     <</OutSlot 5>> setpagedevice"
*End
*CloseUI: *OutputBin


*OpenUI *Duplex/Duplex: PickOne
*DefaultDuplex: None
*Duplex None/Off: "
        <</Duplex false>> setpagedevice"
*End
*Duplex DuplexS/Booklet: "
        <</Duplex true /Tumble false>> setpagedevice"
*End
*Duplex DuplexT/Tablet: "
        <</Duplex true /Tumble true>> setpagedevice"
*End
*CloseUI: *Duplex

*OpenUI *PaperType/Media Type: PickOne
*DefaultPaperType: Plain
*PaperType Plain/Plain Paper: "
        <</PaperType 0>> setpagedevice"
*End
*PaperType Envelopes/Envelopes: "
        <</PaperType 1>> setpagedevice"
*End
*PaperType Transparencies/Transparencies: "
        <</PaperType 2>> setpagedevice"
*End
*PaperType Labels/Labels: "
        <</PaperType 3>> setpagedevice"
*End
*PaperType Cardstocks/Cardstocks: "
        <</PaperType 4>> setpagedevice"
*End
*PaperType LetterH/Letter Head: "
        <</PaperType 5>> setpagedevice"
*End
*CloseUI: *PaperType

*OpenUI *Option7/Edge Smoothing: PickOne
*DefaultOption7: On
*Option7 Off/Off: "
        <</EET 0>> setpagedevice"
*End
*Option7 On/On: "
        <</EET 1>> setpagedevice"
*End
*CloseUI: *Option7

*OpenUI *Option8/Collate: PickOne
*DefaultOption8: True
*Option8 True/On (turn off in application): "
        <</Collate true>> setpagedevice"
*End
*Option8 False/Off: "
        <</Collate false>> setpagedevice"
*End
*CloseUI: *Option8

*OpenUI *Resolution: PickOne
*DefaultResolution: 600dpi
*Resolution 600dpi/600: "
        <</HWResolution [600 600]>> setpagedevice"
*End
*Resolution 300dpi/300: "
        <</HWResolution [300 300]>> setpagedevice"
*End
*CloseUI: *Resolution


*MaxMediaWidth: "1224"
*MaxMediaHeight: "1224"
*HWMargins: 16 16 16 16



*DefaultTransfer: Null
*Transfer Null: "{ }"
*Transfer Null.Inverse: "{ 1 exch sub }"

*DefaultFont: Courier
*Font Wingdings-Regular: Standard "(001.002)" Standard ROM
*Font Albertus-Medium: Standard "(001.002)" Standard ROM
*Font AvantGarde-Book: Standard "(001.006)" Standard ROM
*Font AvantGarde-BookOblique: Standard "(001.006)" Standard ROM
*Font AvantGarde-Demi: Standard "(001.007)" Standard ROM
*Font AvantGarde-DemiOblique: Standard "(001.007)" Standard ROM
*Font Bookman-Demi: Standard "(001.003)" Standard ROM
*Font Bookman-DemiItalic: Standard "(001.003)" Standard ROM
*Font Bookman-Light: Standard "(001.003)" Standard ROM
*Font Bookman-LightItalic: Standard "(001.003)" Standard ROM
*Font Courier: Standard "(002.004)" Standard ROM
*Font Courier-Bold: Standard "(002.004)" Standard ROM
*Font Courier-BoldOblique: Standard "(002.004)" Standard ROM
*Font Courier-Oblique: Standard "(002.004)" Standard ROM
*Font Helvetica: Standard "(001.006)" Standard ROM
*Font Helvetica-Bold: Standard "(001.007)" Standard ROM
*Font Helvetica-BoldOblique: Standard "(001.007)" Standard ROM
*Font Helvetica-Narrow: Standard "(001.006)" Standard ROM
*Font Helvetica-Narrow-Bold: Standard "(001.007)" Standard ROM
*Font Helvetica-Narrow-BoldOblique: Standard "(001.007)" Standard ROM
*Font Helvetica-Narrow-Oblique: Standard "(001.006)" Standard ROM
*Font Helvetica-Oblique: Standard "(001.006)" Standard ROM
*Font NewCenturySchlbk-Bold: Standard "(001.009)" Standard ROM
*Font NewCenturySchlbk-BoldItalic: Standard "(001.007)" Standard ROM
*Font NewCenturySchlbk-Italic: Standard "(001.006)" Standard ROM
*Font NewCenturySchlbk-Roman: Standard "(001.007)" Standard ROM
*Font Palatino-Bold: Standard "(001.005)" Standard ROM
*Font Palatino-BoldItalic: Standard "(001.005)" Standard ROM
*Font Palatino-Italic: Standard "(001.005)" Standard ROM
*Font Palatino-Roman: Standard "(001.005)" Standard ROM
*Font Symbol: Special "(001.007)" Special ROM
*Font Times-Bold: Standard "(001.007)" Standard ROM
*Font Times-BoldItalic: Standard "(001.009)" Standard ROM
*Font Times-Italic: Standard "(001.007)" Standard ROM
*Font Times-Roman: Standard "(001.007)" Standard ROM
*Font ZapfChancery-MediumItalic: Standard "(001.007)" Standard ROM
*Font ZapfDingbats: Special "(001.004)" Special ROM
*Font Albertus-ExtraBold: Standard "(001.002)" Standard ROM
*Font AntiqueOlive: Standard "(001.003)" Standard ROM
*Font AntiqueOlive-Italic: Standard "(001.003)" Standard ROM
*Font AntiqueOlive-Bold: Standard "(001.003)" Standard ROM
*Font Clarendon-Condensed-Bold: Standard "(001.002)" Standard ROM
*Font Marigold: Standard "(001.002)" Standard ROM
*Font Coronet: Standard "(001.007)" Standard ROM
*Font CourierHP-Italic: Standard "(001.006)" Standard ROM
*Font CourierHP-BoldItalic: Standard "(001.006)" Standard ROM
*Font CourierHP: Standard "(001.006)" Standard ROM
*Font CourierHP-Bold: Standard "(001.006)" Standard ROM
*Font Garamond-Antiqua: Standard "(001.005)" Standard ROM
*Font Garamond-Halbfett: Standard "(001.005)" Standard ROM
*Font Garamond-Kursiv: Standard "(001.005)" Standard ROM
*Font Garamond-KursivHalbfett: Standard "(001.005)" Standard ROM
*Font LetterGothic: Standard "(001.007)" Standard ROM
*Font LetterGothic-Italic: Standard "(001.007)" Standard ROM
*Font LetterGothic-Bold: Standard "(001.007)" Standard ROM
*Font CGOmega: Standard"(001.009)" Standard ROM
*Font CGOmega-Italic: Standard"(001.009)" Standard ROM
*Font CGOmega-Bold: Standard"(001.009)" Standard ROM
*Font CGOmega-BoldItalic: Standard"(001.009)" Standard ROM
*Font CGTimes: Standard "(001.009)" Standard ROM
*Font CGTimes-Italic: Standard "(001.009)" Standard ROM
*Font CGTimes-Bold: Standard "(001.009)" Standard ROM
*Font CGTimes-BoldItalic: Standard "(001.009)" Standard ROM
*Font Univers-Medium: Standard "(001.008)" Standard ROM
*Font Univers-MediumItalic: Standard "(001.008)" Standard ROM
*Font Univers-Bold: Standard "(001.008)" Standard ROM

---

### Post by dumas33 on 2007-05-03
Does this driver work for anybody?

When I try to set this driver I get answer: 

"Unable to load the requested driver:" What did I wrong?

Please attache working file, or look whats wrong with this driver...

---

