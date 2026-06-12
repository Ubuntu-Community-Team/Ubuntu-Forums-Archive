---
title: "bbc iplayer"
date: 2011-11-17
forum: General Help
---

### Post by Janeleaper on 2011-11-17
Hi.  I've posted on this topic before, but the last time was about a year ago.

The problem, which has proved insoluble over several years now, is that I can't get the BBC iplayer to play "play again" radio programmes.

I am in Canada, so BBC tv is blocked on the iplayer anyway, but I ought to be able to play radio.  I can play "live" radio, but the play again programmes won't play.

I've got over the problem by using Beebotron, but it isn't ideal because Beebotron often stalls.

I also find it frustrating, because other posters on this forum tell me that they don't have this problem.  But the problem has continued through different versions of Ubuntu (I'm currently using 10.04).  And it is common to all my machines (2 Dell desktops and an Inspiron mini).

Could it be my ISP?  Just for fun, I tried using a proxy server with a UK address, but that didn't work either.

---

### Post by hansdown on 2011-11-17
Hi, Janeleaper.

I remember your original post.

Couldn't help then, but some things, get better.

The first screenshot, amazes  me.

They say, to remove 

```
plugin installer
```

Not sure why.

The second link, should be helpful.

[http://ubuntuguide.net/install-bbc-iplayer-desktop-get-live-radiolive-tv-in-ubuntu](http://ubuntuguide.net/install-bbc-iplayer-desktop-get-live-radiolive-tv-in-ubuntu)

---

### Post by Janeleaper on 2011-11-18
It didn't work, but thanks for trying.  I think I'll repost this query on an annual basis.  Sooner or later....

---

### Post by Zill on 2011-11-18
Janeleaper:  You could try [get_iplayer]("http://www.infradead.org/get_iplayer/html/get_iplayer.html") - it's in the repos.

From the [FAQs]("http://linuxcentre.net/getiplayer/faq")...
> Q5) Can I record or stream BBC iPlayer content from outside of the UK.

For TV mostly not; the BBC simply check that you have a UK based IP address before allowing you to get access to the download credentials. However, some of the iPlayer radio, live radio and podcast content is available outside of the UK. The iPlayer radio is typically streamed at lower quality than in the UK.
Note that get-iplayer is a commmand-line application so you will need to run it from the Terminal.  See the [Documentation]("http://linuxcentre.net/getiplayer/documentation") for full instructions.

---

### Post by Janeleaper on 2011-11-19
No that doesn't work either.  It appears to install, but play again radio programmes don't play.  I just get the "content does not appear to be working" message, as per usual.

But thanks for the link.

---

### Post by Zill on 2011-11-19
> **Janeleaper said:**
> No that doesn't work either.  It appears to install, but play again radio programmes don't play.  I just get the "content does not appear to be working" message, as per usual.
Did you follow the instructions in the documentation?  Is this an error message from get_iplayer or something else?  It can be quite difficult to make sense of the actual command syntax needed by get_iplayer so here is an example I have just run to record a program called "junior science" recently broadcast on BBC Radio 4, with the commands shown in red:
```
roger@dino:~$ [COLOR="Red"]get_iplayer --type=radio junior science[/COLOR]
get_iplayer v2.66, Copyright (C) 2008-2010 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.

Matches:
11368:	Junior Science - 2. The Answering Machine, BBC Radio 4, Drama,Radio
12216:	Science Cafe - 08/11/2011, BBC Radio Wales, Factual,Radio,Science & Nature,Science & Technology,Wales
12217:	Science Cafe - 15/11/2011, BBC Radio Wales, Factual,Radio,Science & Nature,Science & Technology,Wales
12218:	Science In Action - 10/11/2011, BBC World Service, Factual,Radio,Science & Nature
12219:	Science In Action - 17/11/2011, BBC World Service, Factual,Radio,Science & Nature

INFO: 5 Matching Programmes

roger@dino:~$ [COLOR="Red"]get_iplayer --get 11368 --output "/home/roger/Desktop/"[/COLOR]
get_iplayer v2.66, Copyright (C) 2008-2010 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.

Matches:
11368:	Junior Science - 2. The Answering Machine, BBC Radio 4, Drama,Radio

INFO: 1 Matching Programmes
INFO: Checking existence of default version
INFO: flashaacstd1,flashaaclow1,wma1 modes will be tried for version default
INFO: Trying flashaacstd1 mode to record radio: Junior Science - 2. The Answering Machine
INFO: File name prefix = Junior_Science_-_2._The_Answering_Machine_b01756jf_default                 
FLVStreamer v1.9
(c) 2009 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
Starting download at: 0.000 kB
Metadata:                  
  duration              900.05
  moovPosition          36
  audiocodecid          mp4a
  aacaot                2
  audiosamplerate       44100
  audiochannels         2
tags:
  ©alb                 Junior Science
  aART                  BBC Radio 4 FM
  ©ART                 BBC Radio 4 FM
  ©cmt                 A boy's father buys an early version of an answering machine, with chilling consequences.
  cprt                  British Broadcasting Corporation © 2011, all rights reserved.
  ©gen                 Podcast
  ©nam                 Junior Science 18 11 2011
  ©day                 2011
trackinfo:
  length                39692288
  timescale             44100
  language              und
sampledescription:
  sampletype            mp4a
14707.510 kB / 900.03 sec (100.0%)
Download complete
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Sep 16 2011 17:04:18, gcc: 4.4.3
Input #0, flv, from '/home/roger/Desktop/Junior_Science_-_2._The_Answering_Machine_b01756jf_default.partial.aac.flv':
  Duration: 00:15:00.05, start: 0.000000, bitrate: N/A
    Stream #0.0: Audio: aac, 44100 Hz, stereo, s16
Output #0, adts, to '/home/roger/Desktop/Junior_Science_-_2._The_Answering_Machine_b01756jf_default.partial.aac':
    Stream #0.0: Audio: 0x0000, 44100 Hz, stereo, s16
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=   14328kB time=900.05 bitrate= 130.4kbits/s    
video:0kB audio:14063kB global headers:0kB muxing overhead 1.884148%
INFO: Recorded /home/roger/Desktop/Junior_Science_-_2._The_Answering_Machine_b01756jf_default.aac

INFO: id3 tagging aac file
roger@dino:~$ 
```
This has produced a file on my desktop entitled "Junior_Science_-_2._The_Answering_Machine_b01756jf_default.aac".  When clicked on, my default audio application Totem plays back the file.

If you still have problems please post back all the terminal output you receive when running a similar test - preferably using the same radio program (Junior Science) for comparison.  Note that the program ID number is dynamic and changes with time so it is possible that you will see a different ID number to 11368.

---

### Post by Janeleaper on 2011-11-19
Thanks for that, but there's not much point of using such an elaborate way of getting a programme to play, when I can use Beebotron.  What I was hoping for was to be able to play back a programme from the BBC radio site, or the iplayer in the normal way.

---

### Post by Janeleaper on 2011-11-19
> Added: 12861:	Tom Lowe - 19/11/2011, BBC Gloucestershire, Music,News,Radio,Sport
Added: 12862:	Tom Morton - Children in Need Special, BBC Radio Scotland, Entertainment,Music,Pop & Chart,Radio,Rock & Indie,Scotland
Added: 12863:	Tom Morton - 15/11/2011, BBC Radio Scotland, Entertainment,Music,Pop & Chart,Radio,Rock & Indie,Scotland
Added: 12864:	Tom Morton - 16/11/2011, BBC Radio Scotland, Entertainment,Music,Pop & Chart,Radio,Rock & Indie,Scotland
Added: 12865:	Tom Morton - 17/11/2011, BBC Radio Scotland, Entertainment,Music,Pop & Chart,Radio,Rock & Indie,Scotland
Added: 12866:	Tom Morton - 14/11/2011, BBC Radio Scotland, Entertainment,Music,Pop & Chart,Radio,Rock & Indie,Scotland
Added: 12867:	Tom Ravenscroft - 18/11/2011, BBC 6 Music, Dance & Electronica,Experimental & New,Experimental & New,Music,Radio,Rock & Indie
Added: 12868:	Tommy Sandhu - Bollywood playback singer KK, BBC Asian Network, Bhangra,Bollywood,Desi,Entertainment,Music,Radio
Added: 12869:	Tommy Sandhu - Bachchan baby celebrations!, BBC Asian Network, Bhangra,Bollywood,Desi,Entertainment,Music,Radio
Added: 12870:	Tommy Sandhu - Muttar of Fact!, BBC Asian Network, Bhangra,Bollywood,Desi,Entertainment,Music,Radio
Added: 12871:	Tommy Sandhu - Children In Need: Show your Spots, BBC Asian Network, Bhangra,Bollywood,Desi,Entertainment,Music,Radio
Added: 12872:	Tommy Sandhu - Monday masti!, BBC Asian Network, Bhangra,Bollywood,Desi,Entertainment,Music,Radio
Added: 12873:	Toni McDonald - 19/11/2011, BBC Hereford & Worcester, Discussion & Talk Shows,Entertainment,Music,Radio,Review Shows
Added: 12874:	Tony Blackburn - 13/11/2011, BBC London, Classic Pop & Rock,Music,Radio
Added: 12875:	Tony Fisher - Meet the Boss: David Chantler, head of the West Mercia Probation Trust, BBC Hereford & Worcester, Entertainment,Factual,Life Stories,Radio
Added: 12876:	Tony Fisher - Anti-Bullying Week: we hear a story from Hereford, BBC Hereford & Worcester, Entertainment,Factual,Life Stories,Radio
Added: 12877:	Tony Fisher - From the perfect hot pot to what you can find in the fridge to turn your tresses into Cheryl Cole's, BBC Hereford & Worcester, Entertainment,Factual,Life Stories,Radio
Added: 12878:	Tony Fisher - Graham Dilley's Memorial from team mate Mike Gatting, BBC Hereford & Worcester, Entertainment,Factual,Life Stories,Radio
Added: 12879:	Tony Fisher - The perfect Christmas outfit but not the "little black dress" this year, BBC Hereford & Worcester, Entertainment,Factual,Life Stories,Radio
Added: 12880:	Tony Fisher - It's Children-in-Need day!  We try to break a Guinness World Record, BBC Hereford & Worcester, Entertainment,Factual,Life Stories,Radio
Added: 12881:	Tony Livesey - Children in Need Rocks Manchester, BBC Radio 5 live, News,Radio,Sport
Added: 12882:	Tony Livesey - 14/11/2011, BBC Radio 5 live, News,Radio,Sport
Added: 12883:	Tony Livesey - 15/11/2011, BBC Radio 5 live, News,Radio,Sport
Added: 12884:	Tony Livesey - 16/11/2011, BBC Radio 5 live, News,Radio,Sport
Added: 12885:	Tony Lyman - 13/11/2011, BBC Derby, Entertainment,Music,Radio
Added: 12886:	Tony Snell in the Morning - 15/11/2011, BBC Merseyside, Entertainment,News,Radio,Sport
Added: 12887:	Tony Snell in the Morning - 14/11/2011, BBC Merseyside, Entertainment,News,Radio,Sport
Added: 12888:	Tony Snell in the Morning - 16/11/2011, BBC Merseyside, Entertainment,News,Radio,Sport
Added: 12889:	Tony Snell in the Morning - 17/11/2011, BBC Merseyside, Entertainment,News,Radio,Sport
Added: 12890:	Tony Snell in the Morning - 18/11/2011, BBC Merseyside, Entertainment,News,Radio,Sport
Added: 12891:	Tony Wadsworth - 19/11/2011, BBC Leicester, Discussion & Talk Shows,Entertainment,Factual,Phone-ins,Radio,Reality
Added: 12892:	Torchwood - Asylum, Popular, Drama,Radio,SciFi & Fantasy
Added: 12893:	Total Football - With David Prentice, chief sports writer of the Liverpool Echo, BBC Merseyside, Football,Radio,Sport
Added: 12894:	Total Football - 14/11/2011, BBC Merseyside, Football,Radio,Sport
Added: 12895:	Total Football - Frank Gamble and Ian Chisnall, BBC Merseyside, Football,Radio,Sport
Added: 12896:	Total Football - 17/11/2011, BBC Merseyside, Football,Radio,Sport
Added: 12897:	Total Sport - 16/11/2011, BBC Newcastle, Football,Radio,Sport
Added: 12898:	Total Sport - 15/11/2011, BBC Newcastle, Football,Radio,Sport
Added: 12899:	Total Sport - 17/11/2011, BBC Newcastle, Football,Radio,Sport
Added: 12900:	Total Sport - 14/11/2011, BBC Newcastle, Football,Radio,Sport
Added: 12901:	Total Sport - 18/11/2011, BBC Newcastle, Football,Radio,Sport
Added: 12902:	Total Sport - 19/11/2011, BBC Newcastle, Football,Radio,Sport
Added: 12903:	Tracey's Jail Mail - 19/11/2011, BBC WM, Discussion & Talk Shows,Entertainment,Radio
Added: 12904:	Trac - 08/11/2011, BBC Radio Cymru, Music,Radio,Wales
Added: 12905:	Trac - 15/11/2011, BBC Radio Cymru, Music,Radio,Wales
Added: 12906:	Travelling Folk - 17/11/2011, BBC Radio Scotland, Europe,Folk,Music,Radio,Scotland,World
Added: 12907:	Treasure Quest Extra Time - Extracts from Treasure Quest Live, BBC Norfolk, Entertainment,Factual,Radio
Added: 12908:	Treasure Quest with Andy Gelder - Jenna 'Bonsai' Benson faces Ankole cattle, Mona Lisa's lips and muddy shoes., BBC Three Counties, Entertainment,Radio
Added: 12909:	Treasure Quest - Thordis Fridriksson stands in, BBC Norfolk, Entertainment,Radio
Added: 12910:	Treasure Quest - 19/11/2011, BBC Northampton, Entertainment,Factual,Radio
Added: 12911:	Trevor Fry - 14/11/2011, BBC Bristol, Discussion & Talk Shows,Entertainment,Music,Radio
Added: 12912:	Trevor Fry - 15/11/2011, BBC Bristol, Discussion & Talk Shows,Entertainment,Music,Radio
Added: 12913:	Trevor Fry - 16/11/2011, BBC Bristol, Discussion & Talk Shows,Entertainment,Music,Radio
Added: 12914:	Trevor Fry - 17/11/2011, BBC Bristol, Discussion & Talk Shows,Entertainment,Music,Radio
Added: 12915:	Trevor Fry - 18/11/2011, BBC Bristol, Discussion & Talk Shows,Entertainment,Music,Radio
Added: 12916:	Trevor Nelson's Soul Show - 16/11/2011, BBC Radio 2, Music,Radio,Soul & Reggae
Added: 12917:	Trevor Nelson - Embarrassing Parents, BBC 1Xtra, Experimental & New,Hip Hop R'n'B & Dancehall,Music,Pop & Chart,Radio
Added: 12918:	Trevor Nelson - What's Your Favourite Vampire Film?, BBC 1Xtra, Experimental & New,Hip Hop R'n'B & Dancehall,Music,Pop & Chart,Radio
Added: 12919:	Trevor Nelson - Are You Feeling Festive?, BBC 1Xtra, Experimental & New,Hip Hop R'n'B & Dancehall,Music,Pop & Chart,Radio
Added: 12920:	Trevor Nelson - It's Twilight Mania!, BBC 1Xtra, Experimental & New,Hip Hop R'n'B & Dancehall,Music,Pop & Chart,Radio
Added: 12921:	Trevor Nelson - 14/11/2011, BBC 1Xtra, Experimental & New,Hip Hop R'n'B & Dancehall,Music,Pop & Chart,Radio
Added: 12922:	Trevor Nelson - 19/11/2011, BBC 1Xtra, Experimental & New,Hip Hop R'n'B & Dancehall,Music,Pop & Chart,Radio
Added: 12923:	Trish Adudu - 19/11/2011, BBC Coventry & Warwickshire, Entertainment,Radio,Review Shows
Added: 12924:	Tro Shàmhchar an Fheasgair - 13/11/2011, BBC Radio Nan Gaidheal, Easy Listening Soundtracks & Musicals,Music,Radio,Scotland
Added: 12925:	Try Time - 17/11/2011, BBC Merseyside, Radio,Rugby League,Sport
Added: 12926:	Tudur Owen - 19/11/2011, BBC Radio Cymru, Comedy,Entertainment,Radio,Sport,Wales
Added: 12927:	Tuesday Night Sport - 15/11/2011, BBC Sheffield, Radio,Sport
Added: 12928:	Twentyman Talks Back - 18/11/2011, BBC Bristol, Radio,Sport
Added: 12929:	Tìr a' Chiùil - 18/11/2011, BBC Radio Nan Gaidheal, Factual,Radio,Scotland
Added: 12930:	UK Black - 16/11/2011, BBC Bristol, Factual,News,Radio
Added: 12931:	UKG M1X with DJ Q - Zed Bias Guest Mix, BBC 1Xtra, Experimental & New,Garage,Guidance,Hip Hop R'n'B & Dancehall,Music,Radio
Added: 12932:	UKG with Cameo - Mz Bratt, Lioness, Lady Leshurr, Baby Blue, A Dot & Flava D, BBC 1Xtra, Experimental & New,Garage,Guidance,Hip Hop R'n'B & Dancehall,Music,Radio
Added: 12933:	Ujima Radio - 12/11/2011, BBC Bristol, Entertainment,Hip Hop R'n'B & Dancehall,Jazz & Blues,Music,Radio,Soul & Reggae,World
Added: 12934:	Ujima Radio - 19/11/2011, BBC Bristol, Entertainment,Hip Hop R'n'B & Dancehall,Jazz & Blues,Music,Radio,Soul & Reggae,World
Added: 12935:	Un-missable - 13/11/2011, BBC Lancashire, Entertainment,Music,Radio
Added: 12936:	Unforgettable - 14/11/2011, BBC Lancashire, Music,Radio
Added: 12937:	Up All Night - 13/11/2011, BBC Radio 5 live, Factual,News,Radio
Added: 12938:	Up All Night - 14/11/2011, BBC Radio 5 live, Factual,News,Radio
Added: 12939:	Up All Night - 15/11/2011, BBC Radio 5 live, Factual,News,Radio
Added: 12940:	Up All Night - 16/11/2011, BBC Radio 5 live, Factual,News,Radio
Added: 12941:	Up All Night - 17/11/2011, BBC Radio 5 live, Factual,News,Radio
Added: 12942:	Up All Night - 18/11/2011, BBC Radio 5 live, Factual,News,Radio
Added: 12943:	Up All Night - 19/11/2011, BBC Radio 5 live, Factual,News,Radio
Added: 12944:	Upfront - 19/11/2011, BBC Merseyside, Entertainment,Radio,Review Shows
Added: 12945:	Vanessa Feltz - 14/11/2011, BBC Radio 2, Classic Pop & Rock,Music,Radio
Added: 12946:	Vanessa Feltz - 15/11/2011, BBC Radio 2, Classic Pop & Rock,Music,Radio
Added: 12947:	Vanessa Feltz - 16/11/2011, BBC Radio 2, Classic Pop & Rock,Music,Radio
Added: 12948:	Vanessa Feltz - 17/11/2011, BBC Radio 2, Classic Pop & Rock,Music,Radio
Added: 12949:	Vanessa Feltz - Nicki Chapman sits in, BBC Radio 2, Classic Pop & Rock,Music,Radio
Added: 12950:	Vanessa Feltz - The Best Of, BBC London, Factual,Radio
Added: 12951:	Vanessa Feltz - Petrol prices and daytime TV, BBC London, Factual,Radio
Added: 12952:	Vanessa Feltz - Housing, cycling and allergies, BBC London, Factual,Radio
Added: 12953:	Vanessa Feltz - Smoking, parking, unemployment and lending money, BBC London, Factual,Radio
Added: 12954:	Vanessa Feltz - School segregation, customer service and cake, BBC London, Factual,Radio
Added: 12955:	Vanessa Feltz - Schools, food waste, clothes fitting and tattoos, BBC London, Factual,Radio
Added: 12956:	Vent: Series 2 - 2. Things to Do Before You Die, BBC 7, Comedy,Radio
Added: 12957:	Vernon Harwood - Remembrance Sunday in Gloucestershire, BBC Gloucestershire, Factual,Radio
Added: 12958:	Vernon Kay - Live from Strictly!, BBC Radio 1, Entertainment,Highlights,Music,Pop & Chart,Radio
Added: 12959:	Vic Galloway - 14/11/2011, BBC Radio Scotland, Music,Radio,Rock & Indie,Scotland
Added: 12960:	Vic Minett - 14/11/2011, BBC Coventry & Warwickshire, Entertainment,Radio,Review Shows
Added: 12961:	Vic Minett - 15/11/2011, BBC Coventry & Warwickshire, Entertainment,Radio,Review Shows
Added: 12962:	Vic Minett - 16/11/2011, BBC Coventry & Warwickshire, Entertainment,Radio,Review Shows
Added: 12963:	Vic Minett - 17/11/2011, BBC Coventry & Warwickshire, Entertainment,Radio,Review Shows
Added: 12964:	Vic Minett - 18/11/2011, BBC Coventry & Warwickshire, Entertainment,Radio,Review Shows
Added: 12965:	Victoria Derbyshire - 14/11/2011, BBC Radio 5 live, Factual,Life Stories,News,Radio
Added: 12966:	Victoria Derbyshire - Brodie Clark, BBC Radio 5 live, Factual,Life Stories,News,Radio
Added: 12967:	Victoria Derbyshire - 16/11/2011, BBC Radio 5 live, Factual,Life Stories,News,Radio
Added: 12968:	Victoria Derbyshire - 17/11/2011, BBC Radio 5 live, Factual,Life Stories,News,Radio
Added: 12969:	Victoria Derbyshire - Sepp Blatter, BBC Radio 5 live, Factual,Life Stories,News,Radio
Added: 12970:	Vintage Top 40 Show - 19/11/2011, BBC Devon, Entertainment,Music,Radio
Added: 12971:	Vintage Vinyl - 13/11/2011, BBC Tees, Classic Pop & Rock,Music,Radio
Added: 12972:	Voices - 14/11/2011, BBC Jersey, Adult,Factual,Learning,Life Stories,News,Radio
Added: 12973:	WM Sport - Post-match - 19/11/2011, BBC WM, Football,Radio,Sport
Added: 12974:	WM Sport - 15/11/2011, BBC WM, Football,Radio,Sport
Added: 12975:	WM Sport - 14/11/2011, BBC WM, Football,Radio,Sport
Added: 12976:	WM Sport - 17/11/2011, BBC WM, Football,Radio,Sport
Added: 12977:	WM Sport - 16/11/2011, BBC WM, Football,Radio,Sport
Added: 12978:	Wah Yan Jee Sing - 16/11/2011, BBC Radio Ulster, Factual,Northern Ireland,Radio
Added: 12979:	Wake Up to Money - 14/11/2011, BBC Radio 5 live, Factual,Money,News,Radio
Added: 12980:	Wake Up to Money - 15/11/2011, BBC Radio 5 live, Factual,Money,News,Radio
Added: 12981:	Wake Up to Money - 16/11/2011, BBC Radio 5 live, Factual,Money,News,Radio
Added: 12982:	Wake Up to Money - 17/11/2011, BBC Radio 5 live, Factual,Money,News,Radio
Added: 12983:	Wake Up to Money - Berlin Talks, BBC Radio 5 live, Factual,Money,News,Radio
Added: 12984:	Wales at Work - 17/11/2011, BBC Radio Wales, Consumer,Factual,Money,Politics,Radio
Added: 12985:	Walk Right Back - 13/11/2011, BBC Cambridgeshire, Entertainment,Music,Radio
Added: 12986:	Wally Webb - 14/11/2011, BBC Norfolk, Entertainment,Music,Radio,Review Shows,Sport
Added: 12987:	Wally Webb - 15/11/2011, BBC Norfolk, Entertainment,Music,Radio,Review Shows,Sport
Added: 12988:	Wally Webb - 16/11/2011, BBC Norfolk, Entertainment,Music,Radio,Review Shows,Sport
Added: 12989:	Wally Webb - 17/11/2011, BBC Norfolk, Entertainment,Music,Radio,Review Shows,Sport
Added: 12990:	Wally Webb - 18/11/2011, BBC Norfolk, Entertainment,Music,Radio,Review Shows,Sport
Added: 12991:	Warhorses of Letters - Episode 4, BBC Radio 4, Comedy,Radio
Added: 12992:	Warm n Easy - Marcia j Ball @ World Reggae Beat, BBC Three Counties, Music,Radio,Soul & Reggae
Added: 12993:	We Got Soul - 14/11/2011, BBC Northampton, Music,Radio,Soul,Soul & Reggae
Added: 12994:	Week in Westminster - 19/11/2011, BBC Radio 4, Factual,Politics,Radio
Added: 12995:	Weekend Bengali - 13/11/2011, BBC Asian Network, Desi,Entertainment,Music,Radio
Added: 12996:	Weekend Breakfast - 13/11/2011, BBC Asian Network, Desi,Entertainment,Music,Radio
Added: 12997:	Weekend Breakfast - Afghanistan Remembrance Special, BBC Radio 5 live, News,Radio,Sport
Added: 12998:	Weekend Breakfast - 19/11/2011, BBC Radio 5 live, News,Radio,Sport
Added: 12999:	Weekend Breakfast - 19/11/2011, BBC Asian Network, Desi,Entertainment,Music,Radio
Added: 13000:	Weekend Extra - 19/11/2011, BBC Radio Ulster, News,Northern Ireland,Radio
Added: 13001:	Weekend Gujarati - 13/11/2011, BBC Asian Network, Desi,Entertainment,Music,Radio
Added: 13002:	Weekend Kick-off - 18/11/2011, BBC Berkshire, Radio,Sport
Added: 13003:	Weekend Mirpuri - 13/11/2011, BBC Asian Network, Desi,Entertainment,Music,Radio
Added: 13004:	Weekend Punjabi - 13/11/2011, BBC Asian Network, Desi,Entertainment,Music,Radio
Added: 13005:	Weekend Sports Preview - 18/11/2011, BBC York, Football,Radio,Sport
Added: 13006:	Weekend Wogan - 13/11/2011, BBC Radio 2, Classic Pop & Rock,Music,Radio
Added: 13007:	West Yorkshire Sport - Post-match - 19/11/2011, BBC Leeds, Football,Radio,Sport
Added: 13008:	West Yorkshire Sport - 14/11/2011, BBC Leeds, Radio,Sport
Added: 13009:	West Yorkshire Sport - 17/11/2011, BBC Leeds, Radio,Sport
Added: 13010:	West Yorkshire Sport - 15/11/2011, BBC Leeds, Radio,Sport
Added: 13011:	West Yorkshire Sport - 16/11/2011, BBC Leeds, Radio,Sport
Added: 13012:	West Yorkshire Sport - 13/11/2011, BBC Leeds, Radio,Sport
Added: 13013:	West Yorkshire Sport - 18/11/2011, BBC Leeds, Radio,Sport
Added: 13014:	Westenders - 13/11/2011, BBC Humberside, Entertainment,Radio
Added: 13015:	Westminster Hour - 13/11/2011, BBC Radio 4, Factual,Politics,Radio
Added: 13016:	Westwood - Kicking off your week!, BBC 1Xtra, Experimental & New,Hip Hop R'n'B & Dancehall,Music,Pop & Chart,Radio
Added: 13017:	Westwood - Birmingham Uni pass through the studio, BBC 1Xtra, Experimental & New,Hip Hop R'n'B & Dancehall,Music,Pop & Chart,Radio
Added: 13018:	Westwood - Kerry D reviews RiRi's London gigs, BBC 1Xtra, Experimental & New,Hip Hop R'n'B & Dancehall,Music,Pop & Chart,Radio
Added: 13019:	Westwood - 18/11/2011, BBC 1Xtra, Experimental & New,Guidance,Hip Hop R'n'B & Dancehall,Music,Pop & Chart,Radio
Added: 13020:	Westwood - 15/11/2011, BBC 1Xtra, Experimental & New,Hip Hop R'n'B & Dancehall,Music,Pop & Chart,Radio
Added: 13021:	Westwood - 19/11/2011, BBC 1Xtra, Experimental & New,Hip Hop R'n'B & Dancehall,Music,Pop & Chart,Radio
Added: 13022:	What the Papers Say - Episode 78, BBC Radio 4, Factual,Politics,Radio
Added: 13023:	What's the Story? - 11/11/2011, BBC Radio Wales, Comedy,Entertainment,Games & Quizzes,News,Radio,Wales
Added: 13024:	What's the Story? - 18/11/2011, BBC Radio Wales, Comedy,Entertainment,Games & Quizzes,News,Radio,Wales
Added: 13025:	Will Banks' Soul Prescription - 13/11/2011, BBC Oxford, Music,Radio,Soul & Reggae
Added: 13026:	William Wright - 14/11/2011, BBC Lincolnshire, Entertainment,News,Radio,Review Shows
Added: 13027:	William Wright - 15/11/2011, BBC Lincolnshire, Entertainment,News,Radio,Review Shows
Added: 13028:	William Wright - 16/11/2011, BBC Lincolnshire, Entertainment,News,Radio,Review Shows
Added: 13029:	William Wright - 17/11/2011, BBC Lincolnshire, Entertainment,News,Radio,Review Shows
Added: 13030:	William Wright - 18/11/2011, BBC Lincolnshire, Entertainment,News,Radio,Review Shows
Added: 13031:	Wilson, Keppel and Several Bettys - -, BBC Radio 4, Radio
Added: 13032:	Wincey Willis - The National Vintage Fishing Tackle Fayre in Redditch and the Medieval Babes at Hereford Cathedral, BBC Hereford & Worcester, Entertainment,Factual,Radio
Added: 13033:	Wind Down Zone - 17/11/2011, BBC Guernsey, Music,Radio
Added: 13034:	Wind Down Zone - 14/11/2011, BBC Guernsey, Music,Radio
Added: 13035:	Wind Down Zone - 16/11/2011, BBC Guernsey, Music,Radio
Added: 13036:	Wind Down Zone - 15/11/2011, BBC Guernsey, Music,Radio
Added: 13037:	Wind Down Zone - 18/11/2011, BBC Guernsey, Music,Radio
Added: 13038:	Witness - Mission to Mars, BBC World Service, News,Radio
Added: 13039:	Witness - The Death of Leonid Brezhnev, BBC World Service, News,Radio
Added: 13040:	Witness - San Salvador offensive, BBC World Service, News,Radio
Added: 13041:	Witness - Student Uprising in Greece in 1973, BBC World Service, News,Radio
Added: 13042:	Witness - Great Lisbon Earthquake, BBC World Service, News,Radio
Added: 13043:	Witness - Cathy Come Home, BBC World Service, News,Radio
Added: 13044:	Witness - Kim Philby the spy, BBC World Service, News,Radio
Added: 13045:	Witness - Nikola Tesla, BBC World Service, News,Radio
Added: 13046:	Woman's Hour Drama - Journey to Starlight Mountain: Episode 1, BBC Radio 4, Drama,Radio
Added: 13047:	Woman's Hour Drama - Journey to Starlight Mountain: Episode 2, BBC Radio 4, Drama,Radio
Added: 13048:	Woman's Hour Drama - Journey to Starlight Mountain: Episode 3, BBC Radio 4, Drama,Radio
Added: 13049:	Woman's Hour Drama - Journey to Starlight Mountain: Episode 4, BBC Radio 4, Drama,Radio
Added: 13050:	Woman's Hour Drama - Journey to Starlight Mountain: Episode 5, BBC Radio 4, Drama,Radio
Added: 13051:	Woman's Hour - 14/11/2011, BBC Radio 4, Factual,Radio
Added: 13052:	Woman's Hour - Diane Keaton; fathers & maternity care; Alison Teale; HPV vaccine, BBC Radio 4, Factual,Radio
Added: 13053:	Woman's Hour - 16/11/2011, BBC Radio 4, Factual,Radio
Added: 13054:	Woman's Hour - 17/11/2011, BBC Radio 4, Factual,Radio
Added: 13055:	Woman's Hour - Expat Thanksgiving, Paternity Fraud, Salisbury Choristers and Women in Business, BBC Radio 4, Factual,Radio
Added: 13056:	Woman's Hour - Weekend Woman's Hour: Sinead Cusack, Diane Keaton and Anita Dobson, BBC Radio 4, Factual,Radio
Added: 13057:	Words and Music - Travellers' Tales, BBC Radio 3, Arts Culture & the Media,Classical,Factual,Music,Radio
Added: 13058:	World Briefing - 13/11/2011, BBC World Service, News,Radio
Added: 13059:	World Briefing - 13/11/2011, BBC World Service, News,Radio
Added: 13060:	World Briefing - 13/11/2011, BBC World Service, News,Radio
Added: 13061:	World Briefing - 13/11/2011, BBC World Service, News,Radio
Added: 13062:	World Briefing - 13/11/2011, BBC World Service, News,Radio
Added: 13063:	World Briefing - 14/11/2011, BBC World Service, News,Radio
Added: 13064:	World Briefing - 14/11/2011, BBC World Service, News,Radio
Added: 13065:	World Briefing - 14/11/2011, BBC World Service, News,Radio
Added: 13066:	World Briefing - 14/11/2011, BBC World Service, News,Radio
Added: 13067:	World Briefing - 14/11/2011, BBC World Service, News,Radio
Added: 13068:	World Briefing - 14/11/2011, BBC World Service, News,Radio
Added: 13069:	World Briefing - 14/11/2011, BBC World Service, News,Radio
Added: 13070:	World Briefing - 15/11/2011, BBC World Service, News,Radio
Added: 13071:	World Briefing - 15/11/2011, BBC World Service, News,Radio
Added: 13072:	World Briefing - 15/11/2011, BBC World Service, News,Radio
Added: 13073:	World Briefing - 15/11/2011, BBC World Service, News,Radio
Added: 13074:	World Briefing - 15/11/2011, BBC World Service, News,Radio
Added: 13075:	World Briefing - 15/11/2011, BBC World Service, News,Radio
Added: 13076:	World Briefing - 15/11/2011, BBC World Service, News,Radio
Added: 13077:	World Briefing - 16/11/2011, BBC World Service, News,Radio
Added: 13078:	World Briefing - 16/11/2011, BBC World Service, News,Radio
Added: 13079:	World Briefing - 16/11/2011, BBC World Service, News,Radio
Added: 13080:	World Briefing - 16/11/2011, BBC World Service, News,Radio
Added: 13081:	World Briefing - 16/11/2011, BBC World Service, News,Radio
Added: 13082:	World Briefing - 16/11/2011, BBC World Service, News,Radio
Added: 13083:	World Briefing - 16/11/2011, BBC World Service, News,Radio
Added: 13084:	World Briefing - 17/11/2011, BBC World Service, News,Radio
Added: 13085:	World Briefing - 17/11/2011, BBC World Service, News,Radio
Added: 13086:	World Briefing - 17/11/2011, BBC World Service, News,Radio
Added: 13087:	World Briefing - 17/11/2011, BBC World Service, News,Radio
Added: 13088:	World Briefing - 17/11/2011, BBC World Service, News,Radio
Added: 13089:	World Briefing - 17/11/2011, BBC World Service, News,Radio
Added: 13090:	World Briefing - 17/11/2011, BBC World Service, News,Radio
Added: 13091:	World Briefing - 18/11/2011, BBC World Service, News,Radio
Added: 13092:	World Briefing - 18/11/2011, BBC World Service, News,Radio
Added: 13093:	World Briefing - 18/11/2011, BBC World Service, News,Radio
Added: 13094:	World Briefing - 18/11/2011, BBC World Service, News,Radio
Added: 13095:	World Briefing - 18/11/2011, BBC World Service, News,Radio
Added: 13096:	World Briefing - 18/11/2011, BBC World Service, News,Radio
Added: 13097:	World Briefing - 18/11/2011, BBC World Service, News,Radio
Added: 13098:	World Briefing - 19/11/2011, BBC World Service, News,Radio
Added: 13099:	World Briefing - 19/11/2011, BBC World Service, News,Radio
Added: 13100:	World Briefing - 19/11/2011, BBC World Service, News,Radio
Added: 13101:	World Briefing - 19/11/2011, BBC World Service, News,Radio
Added: 13102:	World Briefing - 19/11/2011, BBC World Service, News,Radio
Added: 13103:	World Business Report - 13/11/2011, BBC World Service, Factual,Money,Radio
Added: 13104:	World Business Report - 14/11/2011, BBC World Service, Factual,Money,Radio
Added: 13105:	World Business Report - 14/11/2011, BBC World Service, Factual,Money,Radio
Added: 13106:	World Business Report - 15/11/2011, BBC World Service, Factual,Money,Radio
Added: 13107:	World Business Report - 15/11/2011, BBC World Service, Factual,Money,Radio
Added: 13108:	World Business Report - 15/11/2011, BBC World Service, Factual,Money,Radio
Added: 13109:	World Business Report - 16/11/2011, BBC World Service, Factual,Money,Radio
Added: 13110:	World Business Report - 16/11/2011, BBC World Service, Factual,Money,Radio
Added: 13111:	World Business Report - 16/11/2011, BBC World Service, Factual,Money,Radio
Added: 13112:	World Business Report - 17/11/2011, BBC World Service, Factual,Money,Radio
Added: 13113:	World Business Report - 17/11/2011, BBC World Service, Factual,Money,Radio
Added: 13114:	World Business Report - 17/11/2011, BBC World Service, Factual,Money,Radio
Added: 13115:	World Business Report - 18/11/2011, BBC World Service, Factual,Money,Radio
Added: 13116:	World Business Report - 18/11/2011, BBC World Service, Factual,Money,Radio
Added: 13117:	World Business Report - 19/11/2011, BBC World Service, Factual,Money,Radio
Added: 13118:	World Football - Kosovo, Republic of Ireland and Bob Bradley, BBC World Service, Radio,Sport
Added: 13119:	World Have Your Say - WHYS 30: Arab League suspends Syria, BBC World Service, News,Radio
Added: 13120:	World Have Your Say - WHYS 60: The rise of the "technocracy", BBC World Service, News,Radio
Added: 13121:	World Have Your Say - WHYS 30: New York police clear Occupy camp, BBC World Service, News,Radio
Added: 13122:	World Have Your Say - WHYS 60: The future of the occupy movement, BBC World Service, News,Radio
Added: 13123:	World Have Your Say - WHYS 30: Beginning of the end for Assad?, BBC World Service, News,Radio
Added: 13124:	World Have Your Say - WHYS 60: Will the year 2011 stand out in history?, BBC World Service, News,Radio
Added: 13125:	World Have Your Say - WHYS 30: Should Sepp Blatter resign?, BBC World Service, News,Radio
Added: 13126:	World Have Your Say - WHYS 60: What's going on in Syria? And how should the region respond?, BBC World Service, News,Radio
Added: 13127:	World Have Your Say - WHYS30: Is Burma ready for change?, BBC World Service, News,Radio
Added: 13128:	World Have Your Say - WHYS 60: Syria & Sepp Blatter, BBC World Service, News,Radio
Added: 13129:	World Routes - WOMEX 2011: 1. WOMEX 2011, BBC Radio 3, Music,Radio,World
Added: 13130:	World Update - 14/11/2011, BBC World Service, News,Radio
Added: 13131:	World Update - 15/11/2011, BBC World Service, News,Radio
Added: 13132:	World Update - 16/11/2011, BBC World Service, News,Radio
Added: 13133:	World Update - 17/11/2011, BBC World Service, News,Radio
Added: 13134:	World Update - 18/11/2011, BBC World Service, News,Radio
Added: 13135:	World at One - 14/11/2011, BBC Radio 4, News,Radio
Added: 13136:	World at One - 15/11/2011, BBC Radio 4, News,Radio
Added: 13137:	World at One - 16/11/2011, BBC Radio 4, News,Radio
Added: 13138:	World at One - 17/11/2011, BBC Radio 4, News,Radio
Added: 13139:	World at One - 18/11/2011, BBC Radio 4, News,Radio
Added: 13140:	World on 3 - Muzsikas Session, BBC Radio 3, Folk,Music,Radio,World
Added: 13141:	Wythnos i'w Chofio - 12/11/2011, BBC Radio Cymru, Entertainment,Radio,Wales
Added: 13142:	Wythnos i'w Chofio - 19/11/2011, BBC Radio Cymru, Entertainment,Radio,Wales
Added: 13143:	Yorkshire Brass - 13/11/2011, BBC Leeds, Music,Radio
Added: 13144:	You and Yours - Increases to tax on petrol and flood insurance, BBC Radio 4, Consumer,Factual,Radio
Added: 13145:	You and Yours - Call You and Yours - the rising price of fuel - how can we adapt?, BBC Radio 4, Consumer,Factual,Radio
Added: 13146:	You and Yours - Cutting sickness absence from work and coins that don't work in parking meters, BBC Radio 4, Consumer,Factual,Radio
Added: 13147:	You and Yours - Martha Lane Fox on improving web access for disabled people., BBC Radio 4, Consumer,Factual,Radio
Added: 13148:	You and Yours - Will you be spending less on your children this Christmas?, BBC Radio 4, Consumer,Factual,Radio
Added: 13149:	Your Call with Jim Traynor - 19/11/2011, BBC Radio Scotland, Football,Radio,Scotland,Sport
Added: 13150:	Your Country - 13/11/2011, BBC Sheffield, Country,Music,Radio
Added: 13151:	Your Place and Mine - 19/11/2011, BBC Radio Ulster, Factual,Northern Ireland,Radio
Added: 13152:	Your Shout - 14/11/2011, BBC London, Radio,Sport
Added: 13153:	Your World - A Short History Of Story: Episode 2, BBC World Service, Factual,Radio
Added: 13154:	Your World - The Boy With the Violin, BBC World Service, Factual,Radio
Added: 13155:	Yr Oedfa - 13/11/2011, BBC Radio Cymru, Radio,Religion & Ethics,Wales
Added: 13156:	Yr Wyl Gerdd Dant - -, BBC Radio Cymru, Arts Culture & the Media,Entertainment,Factual,Radio,Wales
Added: 13157:	Zane Lowe - Gig Night with Mumford & Sons, BBC Radio 1, Dance & Electronica,Experimental & New,Experimental & New,Hip Hop,Hip Hop R'n'B & Dancehall,Music,Radio,Rock & Indie
Added: 13158:	Zane Lowe - Skrillex Live In The Studio, BBC Radio 1, Dance & Electronica,Experimental & New,Experimental & New,Hip Hop,Hip Hop R'n'B & Dancehall,Music,Radio,Rock & Indie
Added: 13159:	Zane Lowe - Frank Ocean In Conversation, BBC Radio 1, Dance & Electronica,Experimental & New,Experimental & New,Hip Hop,Hip Hop R'n'B & Dancehall,Music,Radio,Rock & Indie
Added: 13160:	Zoe Ball - 19/11/2011, BBC Radio 2, Classic Pop & Rock,Music,Pop & Chart,Radio
Added: 13161:	iPM - 19/11/2011, BBC Radio 4, Factual,Radio
Matches:
11361:	Junior Science - 2. The Answering Machine, BBC Radio 4, Drama,Highlights,Radio
12211:	Science Cafe - 08/11/2011, BBC Radio Wales, Factual,Radio,Science & Nature,Science & Technology,Wales
12212:	Science Cafe - 15/11/2011, BBC Radio Wales, Factual,Radio,Science & Nature,Science & Technology,Wales
12213:	Science In Action - 10/11/2011, BBC World Service, Factual,Radio,Science & Nature
12214:	Science In Action - 17/11/2011, BBC World Service, Factual,Radio,Science & Nature

INFO: 5 Matching Programmes
jane@jane-desktop:~$ 

Was what was produced on my terminal, but nothing appeared on my desktop.

---

### Post by Janeleaper on 2011-11-19
> jane@jane-desktop:~$  get_iplayer --get 11368 --output "/home/roger/Desktop/"
get_iplayer v2.66, Copyright (C) 2008-2010 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.

Matches:
11368:	radio, Katie Martin - 17/11/2011, BBC Solent, Music,Radio

INFO: 1 Matching Programmes
INFO: Checking existence of default version
INFO: flashaudio1,wma1 modes will be tried for version default
INFO: Trying flashaudio1 mode to record radio: Katie Martin - 17/11/2011

WARNING: ffmpeg does not exist - not converting flv file
INFO: File name prefix = Katie_Martin_-_17_11_2011_p00lgyvc_default                 
FLVStreamer v1.9
(c) 2009 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Failed to open file! /Katie_Martin_-_17_11_2011_p00lgyvc_default.partial.flv
INFO: Command exit code 1 (raw code = 256)
WARNING: Failed to stream file /Katie_Martin_-_17_11_2011_p00lgyvc_default.partial.flv via RTMP
INFO: skipping flashaudio1 mode
INFO: Trying wma1 mode to record radio: Katie Martin - 17/11/2011
INFO: File name prefix = Katie_Martin_-_17_11_2011_p00lgyvc_default                 
INFO: Streaming to file /Katie_Martin_-_17_11_2011_p00lgyvc_default_part01.wma
WARNING: Failed, retrying to stream /Katie_Martin_-_17_11_2011_p00lgyvc_default_part01.wma, exit code: 256
WARNING: Failed, retrying to stream /Katie_Martin_-_17_11_2011_p00lgyvc_default_part01.wma, exit code: 256
WARNING: Failed, retrying to stream /Katie_Martin_-_17_11_2011_p00lgyvc_default_part01.wma, exit code: 256
ERROR: Record thread failed after 3 retries for /Katie_Martin_-_17_11_2011_p00lgyvc_default_part01.wma (renamed to /Katie_Martin_-_17_11_2011_p00lgyvc_default_part01.wma.failed)
INFO: Thread #1 Recorded 0.00MB in 00:00:16 at     0kbps to /Katie_Martin_-_17_11_2011_p00lgyvc_default_part01.wma
INFO: All streaming threads completed
INFO: skipping wma1 mode
ERROR: Failed to record 'Katie Martin - 17/11/2011 (p00lgyvc)'
jane@jane-desktop:~$ 


Sorry, did not reproduce the entire terminal readout.  The rest is above.

---

### Post by Janeleaper on 2011-11-19
And this time I think I managed to get the syntax right, but it still didn't work:

> jane@jane-desktop:~$ get_iplayer --type=radio saturday play
get_iplayer v2.66, Copyright (C) 2008-2010 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.

Matches:
11890:	Phil Kennedy on Saturday - 19/11/2011, BBC Oxford, Entertainment,Radio,Review Shows
12192:	Saturday Breakfast with Jane Smith - 19/11/2011, BBC Cambridgeshire, Entertainment,Radio
12193:	Saturday Breakfast - 19/11/2011, BBC Sheffield, Entertainment,News,Radio,Review Shows
12194:	Saturday Breakfast - 19/11/2011, BBC Newcastle, Factual,Radio
12195:	Saturday Breakfast - 19/11/2011, BBC Somerset, Entertainment,Radio,Review Shows
12196:	Saturday Breakfast - 19/11/2011, BBC Bristol, Entertainment,News,Radio
12197:	Saturday Breakfast - Leek roundabout campaign continues, BBC Stoke, Entertainment,Radio,Review Shows
12198:	Saturday Classics - Simon Russell Beale: 3. St Petersburg, BBC Radio 3, Classical,Music,Radio
12199:	Saturday Edition - 19/11/2011, BBC Radio 5 live, Factual,News,Radio,Science & Nature,Science & Technology
12200:	Saturday Live - Sir Alan Parker, Kate Fox, jailed mother Fiona, Kirsty Young's music, magician Fergus Anckorn, Celia Birtwell, BBC Radio 4, Factual,Families & Relationships,Life Stories,Radio
12201:	Saturday Magazine - 19/11/2011, BBC Radio Ulster, Arts Culture & the Media,Factual,Food & Drink,Lifestyle & Leisure,Northern Ireland,Radio
12202:	Saturday Night with Jim Hawkins - 19/11/2011, BBC Shropshire, Music,Radio
12203:	Saturday Play - The Weirdstone of Brisingamen, BBC Radio 4, Action & Adventure,Drama,Highlights,Popular,Radio,SciFi & Fantasy
12204:	Saturday Review - 19/11/2011, BBC Radio 4, Arts Culture & the Media,Factual,Radio
12205:	Saturday Sport - The Post-match - 19/11/2011, BBC Cambridgeshire, Radio,Sport
12206:	Saturday Sport - 19/11/2011, BBC Kent, Radio,Sport
12207:	Saturday Surgery - 19/11/2011, BBC Bristol, Factual,Health & Wellbeing,Lifestyle & Leisure,Radio
12319:	Solid Gold Saturday with Melvyn Prior - 19/11/2011, BBC Lincolnshire, Entertainment,Radio,Review Shows
12335:	Sounds Like Saturday Night - 19/11/2011, BBC Lancashire, Entertainment,News,Radio
12450:	Stuart George on Saturday - 19/11/2011, BBC Stoke, Entertainment,Music,Radio,Review Shows
10117:	Afternoon Play: Brief Lives - Series 4 - Episode 5, BBC Radio 4, Drama,Legal & Courtroom,Radio
10118:	Afternoon Play - Incident at Boulonvilliers, BBC Radio 4, Drama,Historical,Radio,War & Disaster
10119:	Afternoon Play - Wednesdays with Strangers, BBC Radio 4, Drama,Radio
10120:	Afternoon Play - Love in A Glass Jar, BBC Radio 4, Drama,Radio
10121:	Afternoon Play - A Dose of Fame, BBC Radio 4, Biographical,Drama,Radio
10122:	Afternoon Play - Lost Property: 1. The Wrong Label, BBC Radio 4, Drama,Radio
11790:	Now Playing @6Music - Roots Manuva 'Tweet In', BBC 6 Music, Music,Pop & Chart,Radio,Rock & Indie
11924:	Play It Again - 17/11/2011, BBC Lancashire, Entertainment,Music,Radio
12745:	The Stanley Baxter Playhouse: Series 4 - 1. The Porter's Story, BBC Radio 4, Drama,Radio

INFO: 29 Matching Programmes
jane@jane-desktop:~$ get_iplayer --get 12203 --output "/home/jane/desktop/"
get_iplayer v2.66, Copyright (C) 2008-2010 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.

Matches:
12203:	radio, Saturday Play - The Weirdstone of Brisingamen, BBC Radio 4, Action & Adventure,Drama,Highlights,Popular,Radio,SciFi & Fantasy

INFO: 1 Matching Programmes
INFO: Checking existence of default version
INFO: flashaaclow1,wma1 modes will be tried for version default
INFO: Trying flashaaclow1 mode to record radio: Saturday Play - The Weirdstone of Brisingamen

WARNING: ffmpeg does not exist - not converting flv file
INFO: File name prefix = Saturday_Play_-_The_Weirdstone_of_Brisingamen_b016vxyz_default                 
FLVStreamer v1.9
(c) 2009 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Failed to open file! /Saturday_Play_-_The_Weirdstone_of_Brisingamen_b016vxyz_default.partial.flv
INFO: Command exit code 1 (raw code = 256)
WARNING: Failed to stream file /Saturday_Play_-_The_Weirdstone_of_Brisingamen_b016vxyz_default.partial.flv via RTMP
INFO: skipping flashaaclow1 mode
INFO: Trying wma1 mode to record radio: Saturday Play - The Weirdstone of Brisingamen
INFO: File name prefix = Saturday_Play_-_The_Weirdstone_of_Brisingamen_b016vxyz_default                 
INFO: Streaming to file /Saturday_Play_-_The_Weirdstone_of_Brisingamen_b016vxyz_default_part01.wma
WARNING: Failed, retrying to stream /Saturday_Play_-_The_Weirdstone_of_Brisingamen_b016vxyz_default_part01.wma, exit code: 256
WARNING: Failed, retrying to stream /Saturday_Play_-_The_Weirdstone_of_Brisingamen_b016vxyz_default_part01.wma, exit code: 256
WARNING: Failed, retrying to stream /Saturday_Play_-_The_Weirdstone_of_Brisingamen_b016vxyz_default_part01.wma, exit code: 256
ERROR: Record thread failed after 3 retries for /Saturday_Play_-_The_Weirdstone_of_Brisingamen_b016vxyz_default_part01.wma (renamed to /Saturday_Play_-_The_Weirdstone_of_Brisingamen_b016vxyz_default_part01.wma.failed)
INFO: Thread #1 Recorded 0.00MB in 00:00:11 at     0kbps to /Saturday_Play_-_The_Weirdstone_of_Brisingamen_b016vxyz_default_part01.wma
INFO: All streaming threads completed
INFO: skipping wma1 mode
ERROR: Failed to record 'Saturday Play - The Weirdstone of Brisingamen (b016vxyz)'
jane@jane-desktop:~$ 

---

### Post by Zill on 2011-11-20
> **Janeleaper said:**
> And this time I think I managed to get the syntax right, but it still didn't work:
...WARNING: ffmpeg does not exist - not converting flv file...
You are on the right track.  It may be that you have not got all the required codecs etc installed.  I suggest you install ubuntu-restricted-extras:
```
sudo apt-get install ubuntu-restricted-extras
```
I am not sure if this includes ffmpeg so you may also want to install this separately to be sure:
```
sudo apt-get install ffmpeg
```
You could, of course use synaptic first to see if these two packages are already installed. ;-)

With restricted-extras and ffmpeg installed, please re-run your test example (or mine!) and post the terminal output.  I suggest you use "CODE" tags, rather than "QUOTE" tags, as this enables scrolling within the box.

---

### Post by Zill on 2011-11-20
> **Janeleaper said:**
> And this time I think I managed to get the syntax right, but it still didn't work:
...
jane@jane-desktop:~$ get_iplayer --get 12203 --output "/home/jane/[COLOR="Red"]desktop[/COLOR]/"
...

The Ubuntu 10.04 home desktop directory is actually called "Desktop", *not* "desktop".  Unless you have previously changed this you may have difficulty finding your output file. ;-)

Linux is case-sensitive:  THIS is different to This which is different to this.

---

### Post by Janeleaper on 2011-11-20
> jane@jane-desktop:~$  get_iplayer --type=radio junior science
get_iplayer v2.66, Copyright (C) 2008-2010 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.

Matches:
11361:	Junior Science - 2. The Answering Machine, BBC Radio 4, Drama,Highlights,Radio
12209:	Science Cafe - 15/11/2011, BBC Radio Wales, Factual,Radio,Science & Nature,Science & Technology,Wales
12210:	Science In Action - 10/11/2011, BBC World Service, Factual,Radio,Science & Nature
12211:	Science In Action - 17/11/2011, BBC World Service, Factual,Radio,Science & Nature

INFO: 4 Matching Programmes
jane@jane-desktop:~$  get_iplayer --get 11361 --output "/home/jane/Desktop/"
get_iplayer v2.66, Copyright (C) 2008-2010 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.

Matches:
11361:	radio, Junior Science - 2. The Answering Machine, BBC Radio 4, Drama,Highlights,Radio

INFO: 1 Matching Programmes
INFO: Checking existence of default version
INFO: flashaaclow1,wma1 modes will be tried for version default
INFO: Trying flashaaclow1 mode to record radio: Junior Science - 2. The Answering Machine
INFO: File name prefix = Junior_Science_-_2._The_Answering_Machine_b01756jf_default                 
FLVStreamer v1.9
(c) 2009 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
Starting download at: 0.000 kB
Metadata:                  
  duration              900.14
  moovPosition          36
  audiocodecid          mp4a
  aacaot                2
  audiosamplerate       22050
  audiochannels         1
tags:
  ©alb                 Junior Science
  aART                  BBC Radio 4 FM
  ©ART                 BBC Radio 4 FM
  ©cmt                 A boy's father buys an early version of an answering machine, with chilling consequences.
  cprt                  British Broadcasting Corporation © 2011, all rights reserved.
  ©gen                 Podcast
  ©nam                 Junior Science 18 11 2011
  ©day                 2011
trackinfo:
  length                39696384
  timescale             44100
  language              und
sampledescription:
  sampletype            mp4a
5461.766 kB / 878.36 sec (97.6%)
Download complete
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Sep 16 2011 17:04:18, gcc: 4.4.3
Input #0, flv, from '/home/jane/Desktop/Junior_Science_-_2._The_Answering_Machine_b01756jf_default.partial.aac.flv':
  Duration: 00:15:00.14, start: 0.000000, bitrate: N/A
    Stream #0.0: Audio: aac, 22050 Hz, mono, s16
Output #0, adts, to '/home/jane/Desktop/Junior_Science_-_2._The_Answering_Machine_b01756jf_default.partial.aac':
    Stream #0.0: Audio: libfaac, 22050 Hz, mono, s16
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=    5407kB time=900.14 bitrate=  49.2kbits/s    
video:0kB audio:5274kB global headers:0kB muxing overhead 2.512207%
INFO: Recorded /home/jane/Desktop/Junior_Science_-_2._The_Answering_Machine_b01756jf_default.aac

INFO: id3 tagging aac file
jane@jane-desktop:~$ 


Brilliant!  It worked.  Thanks.

---

### Post by Zill on 2011-11-20
> **Janeleaper said:**
> Brilliant!  It worked.  Thanks.
You're welcome. :-)  I'm glad it all worked in the end.

Hope you don't find a couple of commands and a click *too* clunky!  I know it's not quite as intuitive as a GUI but I have found that get_iplayer is a fast and useful tool to grab a BBC programme for future listening/viewing.

---

### Post by Janeleaper on 2011-12-05
By chance, I've just discovered the solution to my original query, and why several posters on this forum have told me that they don't have the difficulty I've experienced playing "play again" BBC radio programmes. I'll explain in detail, in case anyone else has this problem.

If I go to the BBC radio schedule and select the iplayer link for a programme that has already played, the iplayer opens but the programme does not play.

However, if I select the "listen" link at the top of the page, which links to "live" radio, then the iplayer opens and live radio plays.

Up until now, that was all I'd done.  I've now discovered, that if I get the "live" radio playing, and **then** select the "play again link", the iplayer switches from live radio to the play again programme and actually plays it.

In other words, you have to get the iplayer playing live radio before selecting a "play again" link without closing the iplayer first.

---

### Post by Zill on 2011-12-05
> **Janeleaper said:**
> ...If I go to the BBC radio schedule and select the iplayer link for a programme that has already played, the iplayer opens but the programme does not play...
Earlier programmes seems to play OK for me if I just click on the appropriate "Listen now" link. However, I do live in the UK so this is not surprising.

Your workaround should be useful for users outside the UK, where the iPlayer service may be more restricted.  Thank you for updating this thread.

---

### Post by Janeleaper on 2011-12-06
There does seem to be a difference between the iplayer radio in the UK and outside it.  I think there was some technical information about this on the Beebotron.org site, but it seems to be down at the moment and I can't access it.

---

