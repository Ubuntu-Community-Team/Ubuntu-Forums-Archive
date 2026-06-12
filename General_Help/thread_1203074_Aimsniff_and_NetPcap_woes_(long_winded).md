---
title: "Aimsniff and Net:Pcap woes (long winded)"
date: 2009-07-02
forum: General Help
---

### Post by kapu222 on 2009-07-02
Hello fellow unix people.
What follows is a pretty daunting task, just to try and articulate this problem gives me a headache.
I have spent the whole day installing Aimsniff on 2.6.28-13-server #44-Ubuntu SMP.
I have spent a good deal of time reading old posts from here, and other forums. The aimsniff.com user forum doesn't seem to work. Even google cache has the phpBB error that is on [http://aimsniff.com/forum/index.php](http://aimsniff.com/forum/index.php)

(Just to make it clear, I'm NOT a nosy script-kiddie. I am a parent. I don't want to be draconian and strictly forbid chat in my house. I wish to be able to log conversations for minors using chat in my house. I hate to do it but chat is potentially dangerous. It will be nice to have a big log of everything. It will help keep my mind at ease)

I have run into major problems installing Net:pcap for perl, as have many many others.
(see [http://www.aimsniff.com/documentation/AIMSniffReadme.txt](http://www.aimsniff.com/documentation/AIMSniffReadme.txt) )

After battling with trying to get some form of Net:pcap installed, It is now the case that both Net-Pcap-0.16 AND Net-Pcap-0.14 are in my /root/.cpan/build/ directory. I am afraid that both are installed, or, maybe none are installed. I just don't know how to tell :-(

This project has been fun so far, but I have stopped making progress after I managed to install all of the perl depends this aimsniff requires. And I think I may have broke something. (Arggggg!)

For those interested, I will write some more about what I am doing/experiencing...


[LIST]
[*] First, I arp poison the target computer and my home router, and make sure I am man in the middle. This is easy and there are no problems there. My Ubuntu box is in the middle.
[/LIST]
 

[LIST]
[*] Second I issue the command to start aimsniff:[I]
./aimSniff.pl -C=/etc/aimsniff.config[/I]
[/LIST]
 
where this is my config:

```
#dumpHandles=1
#dumpfile=/home/emile/aimsniff/aim.dump
#outputFile=./aim.messages
handlefile=./handlesfile
#packetCount=10
#dev=eth0
filter='tcp and port 5190'
promisc=1
timeout=1000
SMB=0
daemon=1
nodb=0
quiet=0
debug=1
useSyslog=1
parentPollTimeout=10
childCPUMaxPct=90
host=localhost
user=aim
password=blahblahblah
database=aimsniff
```After issuing this command I ultimately end up with two new 'processes' running each named /usr/bin/perl -w?
I had to comment out eth0 in the config file because if I activate that line I get an error. It defaults to eth0 anyways.

But, nothing gets dumped to the mysql database. if I do a tcpdump I can see that I am getting the target computer's traffic. And, I have verified that I can connect to the database manually using the name and password.

Apologies for the long winded question. Does anyone have any troubleshooting advice?

**********************************************************************
Some dumps follow
**********************************************************************
**ifconfig -a**
```
eth0      Link encap:Ethernet  HWaddr 00:11:43:66:10:a1  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe66:10a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44452 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54291 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16429990 (16.4 MB)  TX bytes:29901994 (29.9 MB)
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:897 errors:0 dropped:0 overruns:0 frame:0
          TX packets:897 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74218 (74.2 KB)  TX bytes:74218 (74.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0b:7d:11:b1:3f  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-0B-7D-11-B1-3F-00-00-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)   
```**cpan> 'r'**
```
Package namespace         installed    latest  in CPAN file
Archive::Extract               0.24      0.34  KANE/Archive-Extract-0.34.tar.gz
Attribute::Handlers            0.79      0.85  SMUELLER/Attribute-Handlers-0.85.tar.gz
AutoLoader                     5.63      5.68  SMUELLER/AutoLoader-5.68.tar.gz
B::Debug                       1.05      1.11  RURBAN/B-Debug-1.11.tar.gz
B::Lint                        1.09      1.11  JJORE/B-Lint-1.11.tar.gz
CPANPLUS                       0.84    0.8601  KANE/CPANPLUS-0.8601.tar.gz
CPANPLUS::Dist::Build       0.06_02      0.34  BINGOS/CPANPLUS-Dist-Build-0.34.tar.gz
Cairo                         1.060     1.061  TSCH/Cairo-1.061.tar.gz
Class::Accessor                0.31      0.33  KASEI/Class-Accessor-0.33.tar.gz
Config::File                   1.46      1.50  GWOLF/Config-File-1.50.tar.gz
DB_File                     1.816_1     1.820  PMQS/DB_File-1.820.tar.gz
Devel::PPPort                  3.13      3.19  MHX/Devel-PPPort-3.19.tar.gz
Digest                         1.15      1.16  GAAS/Digest-1.16.tar.gz
Digest::MD5                 2.36_01      2.39  GAAS/Digest-MD5-2.39.tar.gz
Encode                         2.23      2.33  DANKOGAI/Encode-2.33.tar.gz
Exporter                       5.62      5.63  FERREIRA/Exporter-5.63.tar.gz
ExtUtils::ParseXS           2.18_02      2.20  DAGOLDEN/ExtUtils-ParseXS-2.20.tar.gz
File::Fetch                    0.14      0.20  KANE/File-Fetch-0.20.tar.gz
File::Path                     2.04      2.07  DLAND/File-Path-2.07.tar.gz
File::chdir                    0.06    0.1002  DAGOLDEN/File-chdir-0.1002.tar.gz
Filter::Simple                 0.82      0.84  SMUELLER/Filter-Simple-0.84.tar.gz
Getopt::Long                   2.37      2.38  JV/Getopt-Long-2.38.tar.gz
Glib                          1.190     1.221  TSCH/Glib-1.221.tar.gz
Gnome2::VFS                   1.080     1.081  TSCH/Gnome2-VFS-1.081.tar.gz
Gtk2                          1.190     1.220  TSCH/Gtk2-1.220.tar.gz
HTML::Parser                   3.59      3.61  GAAS/HTML-Parser-3.61.tar.gz
HTTP::Server::Simple           0.36      0.38  JESSE/HTTP-Server-Simple-0.38.tar.gz
IO                          1.23_01      1.25  GBARR/IO-1.25.tar.gz
IO::Socket::SSL                1.18      1.24  SULLR/IO-Socket-SSL-1.24.tar.gz
IPC::Cmd                     0.40_1      0.46  KANE/IPC-Cmd-0.46.tar.gz
IPC::SysV                      1.05      2.01  MHX/IPC-SysV-2.01.tar.gz
Locale::Maketext               1.12      1.13  FERREIRA/Locale-Maketext-1.13.tar.gz
Log::Message                   0.01      0.02  KANE/Log-Message-0.02.tar.gz
MIME::Base64                3.07_01      3.08  GAAS/MIME-Base64-3.08.tar.gz
Math::BigInt                   1.88      1.89  TELS/math/Math-BigInt-1.89.tar.gz
Math::BigInt::FastCalc         0.16      0.19  TELS/math/Math-BigInt-FastCalc-0.19.tar.gz
Math::BigRat                   0.21      0.22  TELS/math/Math-BigRat-0.22.tar.gz
Math::Complex                  1.37      1.56  JHI/Math-Complex-1.56.tar.gz
Module::CoreList               2.13      2.17  RGARCIA/Module-CoreList-2.17.tar.gz
Module::Load                   0.12      0.16  KANE/Module-Load-0.16.tar.gz
Module::Load::Conditional      0.22      0.30  KANE/Module-Load-Conditional-0.30.tar.gz
Module::Loaded                 0.01      0.02  KANE/Module-Loaded-0.02.tar.gz
Module::Pluggable               3.6       3.9  SIMONW/Module-Pluggable-3.9.tar.gz
NEXT                        0.60_01      0.64  FLORA/NEXT-0.64.tar.gz
Net::LibIDN                    0.07      0.12  THOR/Net-LibIDN-0.12.tar.gz
Net::Pcap                      0.14      0.16  SAPER/Net-Pcap-0.16.tar.gz
Net::Ping                      2.33      2.36  SMPETERS/Net-Ping-2.36.tar.gz
Object::Accessor               0.32      0.34  KANE/Object-Accessor-0.34.tar.gz
Package::Constants             0.01      0.02  KANE/Package-Constants-0.02.tar.gz
Pod::Parser                    1.35      1.37  MAREKR/Pod-Parser-1.38.tar.gz
Pod::Perldoc                3.14_02      3.15  FERREIRA/Pod-Perldoc-3.15.tar.gz
Pod::Simple                    3.05      3.07  ARANDAL/Pod-Simple-3.07.tar.gz
RPC::XML                       1.41      1.42  RJRAY/RPC-XML-0.65.tar.gz
Safe                           2.12      2.17  RGARCIA/Safe-2.17.tar.gz
SelfLoader                     1.11      1.17  SMUELLER/SelfLoader-1.17.tar.gz
Storable                       2.18      2.20  AMS/Storable-2.20.tar.gz
Switch                         2.13      2.14  RGARCIA/Switch-2.14.tar.gz
Sys::Syslog                    0.22      0.27  SAPER/Sys-Syslog-0.27.tar.gz
Term::UI                       0.18      0.20  KANE/Term-UI-0.20.tar.gz
Test::Harness::Straps       0.26_01      0.30  MSCHWERN/Test-Harness-Straps-0.30.tar.gz
Text::ParseWords               3.26      3.27  CHORNY/Text-ParseWords-3.27.zip
Thread::Queue                  2.00      2.11  JDHEDDEN/Thread-Queue-2.11.tar.gz
Thread::Semaphore              2.01      2.09  JDHEDDEN/Thread-Semaphore-2.09.tar.gz
Tie::RefHash                   1.37      1.38  NUFFIN/Tie-RefHash-1.38.tar.gz
Time::HiRes                  1.9711    1.9719  JHI/Time-HiRes-1.9719.tar.gz
Time::Local                    1.18    1.1901  DROLSKY/Time-Local-1.1901.tar.gz
Time::Piece                    1.12      1.15  MSERGEANT/Time-Piece-1.15.tar.gz
URI                            1.37      1.38  GAAS/URI-1.38.tar.gz
WWW::Mechanize                 1.52      1.54  PETDANCE/WWW-Mechanize-1.54.tar.gz
XSLoader                       0.08      0.10  SAPER/XSLoader-0.10.tar.gz
base                           2.13      2.14  RGARCIA/base-2.14.tar.gz
bignum                         0.22      0.23  TELS/math/bignum-0.23.tar.gz
constant                       1.13      1.17  SAPER/constant-1.17.tar.gz
threads                        1.67      1.73  JDHEDDEN/threads-1.73.tar.gz
threads::shared                1.14      1.29  JDHEDDEN/threads-shared-1.29.tar.gz
version                        0.74      0.76  JPEACOCK/version-0.76.tar.gz
B                              1.17      1.19  NWCLARK/perl-5.8.9.tar.gz
CGI                            3.29      3.43  LDS/CGI.pm-3.43.tar.gz
CGI::Carp                      1.29      1.30  LDS/CGI.pm-3.34.tar.gz
ExtUtils::MakeMaker::bytes      6.42       6.5  MSCHWERN/ExtUtils-MakeMaker-6.50.tar.gz
Fatal                          1.05      2.03  PJF/autodie-2.03.tar.gz
Filter::Util::Call             1.07      1.08  PMQS/Filter-1.37.tar.gz
HTML::Form                    5.817     5.827  GAAS/libwww-perl-5.828.tar.gz
Pod::Man                    2.18_01      2.22  RRA/podlators-2.2.2.tar.gz
Term::ANSIColor                1.12      2.00  RRA/ANSIColor-2.00.tar.gz
Text::Tabs                2007.1117 2009.0305  MUIR/modules/Text-Tabs+Wrap-2009.0305.tar.gz
151 installed modules have no parsable version number
(use 'o conf show_unparsable_versions 1' to show them)
```

---

