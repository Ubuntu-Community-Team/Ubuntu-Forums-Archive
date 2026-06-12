---
title: "whois command?"
date: 2012-04-19
forum: General Help
---

### Post by garyed on 2012-04-19
I've run the whois command & found a domain name I want that is expiring.
My question is: does the whois command do anything different that searching the whois database through an online service like whoislookup.com does?
I'm concerned that by using the command I'm alerting someone that I'm interested in the domain. Does the command line whois by-pass any of these services at all?

---

### Post by HiImTye on 2012-04-19
man whois
```
tye@T:~$ man whois > out.txt; cat out.txt
WHOIS(1)                                                                                       Debian GNU/Linux                                                                                      WHOIS(1)



NAME
       whois - client for the whois directory service

SYNOPSIS
       whois [ -h HOST ] [ -p  PORT ] [ -aCFHlLMmrRSVx ] [ -g SOURCE:FIRST-LAST ] [ -i ATTR ] [ -S SOURCE ] [ -T TYPE ] object

       whois [ -t ] [ -v ] template whois [ -q ] keyword

DESCRIPTION
       whois searches for an object in a RFC 3912 database.

       This  version  of  the  whois  client  tries  to  guess  the  right  server  to ask for the specified object. If no guess can be made it will connect to whois.networksolutions.com for NIC handles or
       whois.arin.net for IPv4 addresses and network names.

OPTIONS
       -h HOST Connect to HOST.

       -H      Do not display the legal disclaimers some registries like to show you.

       -p PORT Connect to PORT.

       --verbose
               Be verbose.

       --help  Display online help.

       Other options are flags understood by RIPE-like servers.

NOTES
       Please remember that whois.networksolutions.com by default will only search in the domains database. If you want to search for NIC handles you have to prepend a ! character. When you  do  this,  the
       default server becomes whois.networksolutions.com.

       When querying whois.arin.net for IPv4 or IPv6 networks, the CIDR netmask length will be automatically removed from the query string.

       When querying whois.nic.ad.jp for AS numbers, the program will automatically convert the request in the appropriate format, inserting a space after the string AS.

       When querying whois.denic.de for domain names and no other flags have been specified, the program will automatically add the flag -T dn.

       When querying whois.dk-hostmaster.dk for domain names and no other flags have been specified, the program will automatically add the flag --show-handles.

       RIPE-specific  command  line options are ignored when querying non-RIPE servers. This may or may not be the behaviour intended by the user.  When querying a non-standard server, command line options
       which are not to be interpreted by the client should always follow the -- separator (which marks the beginning of the query string).

       If the /etc/whois.conf config file exists, it will be consulted to find a server before applying the normal rules. Each line of the file should contain a regular expression to be matched against the
       query text and the whois server to use, separated by white space.

       The  whois  protocol  does  not  specify  an encoding for characters which cannot be represented by ASCII and implementations vary wildly.  If the program knows that a specific server uses a certain
       encoding, if needed it will transcode the server output to the encoding specified by the current system locale.

       Command line arguments will always be interpreted accordingly to the current system locale and converted to the IDN ASCII Compatible Encoding.

Files
       /etc/whois.conf

ENVIRONMENT
       LANG   When querying whois.nic.ad.jp and whois.jprs.jp english text is requested unless the LANG or LC_MESSAGES environment variables specify a Japanese locale.

       WHOIS_OPTIONS
              A list of options which will be evalued before the ones specified on the command line.

       WHOIS_SERVER
              This server will be queried if the program cannot guess where some kind of objects are located. If the variable does not exist then whois.arin.net will be queried.

SEE ALSO
       RFC 3912: WHOIS Protocol Specification

       RIPE-223: RIPE NCC Database Documentation

       Detailed help on available flags can be found in RIPE-223 or in the help file which can be obtained with the command:

              whois -h whois.ripe.net HELP

BUGS
       The program may have buffer overflows in the command line parser: be sure to not pass untrusted data to it.  It should be rewritten to use a dynamics strings library.

HISTORY
       This program closely tracks the user interface of the whois client developed at RIPE by Ambrose Magee and others on the base of the original BSD client.  I also added support for the protocol exten&#8208;
       sions developed by David Kessens of QWest for the 6bone server.

AUTHOR
       Whois and this man page were written by Marco d'Itri <md@linux.it> and are licensed under the terms of the GNU General Public License, version 2 or higher.




Marco d'Itri                                                                                   20 December 2009                                                                                      WHOIS(1)
```

---

### Post by garyed on 2012-04-19
I understand the command to some degree but that is really not my question.
I've noticed that looking up domain names from a whois service will sometimes result in that name being registered by someone else after it shows available if you don't grab it right away. What I was wondering is if the command line whois by-passes any database that might monitor those requests or is it no different than searching for a domain name from a browser in that respect.

---

### Post by Cheesemill on 2012-04-19
When you search using a browser you are just using a web front end to run the whois command on a different machine. So no, there is no difference.

---

### Post by IWantFroyo on 2012-04-19
Whoislookup is just running whois anyways. It's really the same thing.

---

### Post by garyed on 2012-04-19
Thanks,

I guess the only difference then is you're not using a third party to run the request if you use the command line whois. If the third party monitors your request then it could make a difference but if the whois database itself is monitored then it wouldn't make a difference unless both parties are monitoring each request.

---

### Post by HiImTye on 2012-04-20
I only linked the man page because it answered your question precisely

---

