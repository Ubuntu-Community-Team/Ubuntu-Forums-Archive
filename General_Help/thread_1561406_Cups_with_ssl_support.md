---
title: "Cups with ssl support"
date: 2010-08-26
forum: General Help
---

### Post by HandleWithCare on 2010-08-26
Hi everyone,

At my university a webprint environment has been setup a while back. While this all works out of the box on window an fairly easy on mac OSX I haven't been able to get this working on ubuntu. The problem is that cups by default does not support ssl (as I have been told). There is a page on how to get this working on ubuntu in dutch: [https://wiki.ubuntu.com/NlTUDelft]("https://wiki.ubuntu.com/NlTUDelft"), which links to another page which has instuctions on how to compile cups with ssl support: [http://www.cse.ust.hk/~lkmpoon/linux/ubuntu-hkust.html]("http://www.cse.ust.hk/~lkmpoon/linux/ubuntu-hkust.html")

When following this guide I get some errors in the "dpkg-buildpackage -rfakeroot -uc -b" step, thus no .deb files are created. These are the contents of the error log:

> 
CUPS 1.4 Software Test Report

This software test report provides detailed test results that are used to evaluate the stability and compliance of the Common UNIX Printing System ("CUPS") Version 1.4.
Document Overview

This software test plan is organized into the following sections:

    * 1 - IPP Compliance Tests
    * 2 - Command Tests
    * 3 - Log Files

1 - IPP Compliance Tests

This section provides the results to the IPP compliance tests outlined in the CUPS Software Test Plan. These tests were run on 2010-08-26 by root on sdy-laptop.

"4.1-requests.test":
    No Attributes                                                [PASS]
        RECEIVED: 116 bytes in response
    Charset Attribute                                            [PASS]
        RECEIVED: 119 bytes in response
    Language Attribute                                           [PASS]
        RECEIVED: 119 bytes in response
    Language + Charset Attributes                                [PASS]
        RECEIVED: 119 bytes in response
    Charset + Language Attributes                                [PASS]
        RECEIVED: 119 bytes in response
    Charset + Language + Printer URI Attributes                  [PASS]
        RECEIVED: 72 bytes in response
    Charset + Language + Job URI Attributes                      [PASS]
        RECEIVED: 117 bytes in response
    Bad IPP Version                                              [PASS]
        RECEIVED: 122 bytes in response

"4.2-cups-printer-ops.test":
    Add Printer Test1                                            [PASS]
        RECEIVED: 72 bytes in response
    Verify Printer Test1 Added                                   [PASS]
        RECEIVED: 4918 bytes in response
    Delete Printer Test1                                         [PASS]
        RECEIVED: 72 bytes in response
    Verify Printer Test1 Deleted                                 [PASS]
        RECEIVED: 126 bytes in response
    Subscribe to Printer Events                                  [PASS]
        RECEIVED: 104 bytes in response
    Add Printer Test2                                            [PASS]
        RECEIVED: 72 bytes in response
    Verify Printer Test2 Added                                   [PASS]
        RECEIVED: 4881 bytes in response
    Modify Printer Test2                                         [PASS]
        RECEIVED: 72 bytes in response
    Re-Add Printer Test1                                         [PASS]
        RECEIVED: 72 bytes in response
    Verify Printer Test1 Re-Added                                [PASS]
        RECEIVED: 5160 bytes in response
    Get Default Printer with no default set                      [PASS]
        RECEIVED: 109 bytes in response
    Set Default Printer to Test1                                 [PASS]
        RECEIVED: 72 bytes in response
    Get Default Printer                                          [PASS]
        RECEIVED: 5160 bytes in response
    Get IPP/2.x Attributes for Printer Test1                     [PASS]
        RECEIVED: 5280 bytes in response

"4.3-job-ops.test":
    Print PostScript Job with bad job-sheets value to Test1      [PASS]
        RECEIVED: 120 bytes in response
    Print PostScript Job to Test1                                [PASS]
        RECEIVED: 174 bytes in response
    Get Job Attributes                                           [PASS]
        RECEIVED: 807 bytes in response
    Print JPEG Job to Test2                                      [FAIL]
        RECEIVED: 174 bytes in response
        status-code = 0000 (successful-ok)
        EXPECTED: notify-subscription-id
        attributes-charset (charset) = "utf-8" 
        attributes-natural-language (naturalLanguage) = "en" 
        job-uri (uri) = "http://sdy-laptop:8631/jobs/30" 
        job-id (integer) = 30 
        job-state (enum) = 3 
        job-state-reasons (keyword) = "none" 

"4.4-subscription-ops.test":
    Add Printer Subscription w/Lease                             [FAIL]
        RECEIVED: 124 bytes in response
        BAD STATUS
        status-code = 0415 (client-error-too-many-subscriptions)
        EXPECTED: notify-subscription-id
        attributes-charset (charset) = "utf-8" 
        attributes-natural-language (naturalLanguage) = "en" 
        status-message (textWithoutLanguage) = "There are too many subscriptions." 

2 - Command Tests

This section provides the results to the command tests outlined in the CUPS Software Test Plan. These tests were run on 2010-08-26 by root on sdy-laptop.

"5.1-lpadmin.sh":
Add Printer Test

    lpadmin -p Test3 -v file:/dev/null -E -m drv:///sample.drv/deskjet.ppd
lpadmin: Unable to copy PPD file!
    FAILED

"5.2-lpc.sh":
LPC Test

    lpc status
Test1:
	printer is on device '/tmp/Test1' speed -1
	queuing is enabled
	printing is enabled
	16 entries
	daemon present
Test2:
	printer is on device '/tmp/Test2' speed -1
	queuing is enabled
	printing is enabled
	13 entries
	daemon present
Test3:
	printer is on device '/dev/null' speed -1
	queuing is enabled
	printing is enabled
	no entries
	daemon present
    PASSED


"5.3-lpq.sh":
LPQ Test

    lpq -P Test1
Test1 is ready
Rank    Owner   Job     File(s)                         Total Size
1st     root    29      Untitled                        17408 bytes
    PASSED


"5.4-lpstat.sh":
LPSTAT Test

    lpstat -t
scheduler is running
system default destination: Test1
device for Test1: /tmp/Test1
device for Test2: /tmp/Test2
device for Test3: /dev/null
Test1 accepting requests since Thu Aug 26 11:43:58 2010
Test2 accepting requests since Thu Aug 26 11:43:58 2010
Test3 accepting requests since Thu Aug 26 11:28:45 2010
printer Test1 is idle.  enabled since Thu Aug 26 11:43:58 2010
	/tmp/cups-root/bin/filter/pstops failed
printer Test2 is idle.  enabled since Thu Aug 26 11:43:58 2010
	/tmp/cups-root/bin/filter/gziptoany failed
printer Test3 is idle.  enabled since Thu Aug 26 11:28:45 2010
Test1-29                root             17408   Thu Aug 26 11:43:58 2010
Test2-30                root            204800   Thu Aug 26 11:43:58 2010
    PASSED

LPSTAT Test

    lpstat -H
    FAILED (localhost:8631
Test1-29                root             17408   Thu Aug 26 11:43:58 2010
Test2-30                root            204800   Thu Aug 26 11:43:58 2010)

"5.5-lp.sh":
LP Default Test

    lp testfile.pdf
request id is Test1-31 (1 file(s))
    PASSED

LP Destination Test

    lp -d Test2 testfile.jpg
request id is Test2-32 (1 file(s))
    PASSED

LP Options Test

    lp -d Test1 -P 1-4 -o job-sheets=classified,classified testfile.pdf
request id is Test1-33 (1 file(s))
    PASSED

LP Flood Test (10 times in parallel)

    lp -d Test1 testfile.jpg
    lp -d Test2 testfile.jpg
request id is Test2-34 (1 file(s))
request id is Test2-35 (1 file(s))
request id is Test1-36 (1 file(s))
request id is Test1-37 (1 file(s))
request id is Test2-38 (1 file(s))
request id is Test1-39 (1 file(s))
request id is Test2-40 (1 file(s))
request id is Test1-41 (1 file(s))
request id is Test2-42 (1 file(s))
request id is Test1-43 (1 file(s))
request id is Test2-44 (1 file(s))
request id is Test1-45 (1 file(s))
request id is Test2-46 (1 file(s))
request id is Test1-47 (1 file(s))
request id is Test1-48 (1 file(s))
request id is Test2-49 (1 file(s))
request id is Test2-50 (1 file(s))
request id is Test1-51 (1 file(s))
request id is Test2-52 (1 file(s))
    PASSED

request id is Test1-53 (1 file(s))
Waiting for jobs to complete...25...

"5.6-lpr.sh":
LPR Default Test

    lpr testfile.pdf
    PASSED

LPR Destination Test

    lpr -P Test2 testfile.jpg
    PASSED

LPR Options Test

    lpr -P Test1 -o number-up=4 -o job-sheets=standard,none testfile.pdf
    PASSED

LPR Flood Test (10 times in parallel)

    lpr -P Test1 testfile.jpg
    lpr -P Test2 testfile.jpg
    PASSED

Waiting for jobs to complete...48...

"5.7-lprm.sh":
LPRM Current Test

    lpr -o job-hold-until=indefinite testfile.jpg
    lprm
    PASSED

LPRM Destination Test

    lpr -P Test1 -o job-hold-until=indefinite testfile.jpg
    lprm Test1
    PASSED


"5.8-cancel.sh":
Cancel Destination Test

    lp -d Test1 -o job-hold-until=indefinite testfile.jpg
request id is Test1-79 (1 file(s))
    cancel Test1
    PASSED

Cancel All Test

    cancel -a
    PASSED


"5.9-lpinfo.sh":
LPINFO Devices Test

    lpinfo -v
    PASSED

LPINFO Drivers Test

    lpinfo -m
lpinfo: Internal Server Error
    FAILED

3 - Log Files
Summary

PASS: Printer 'Test1' correctly produced 0 page(s).

FAIL: Printer 'Test2' produced 0 page(s), expected 23.

PASS: requests logged.

PASS: CUPS-Get-Default not logged.

PASS: 0 emergency messages.

PASS: 0 alert messages.

PASS: 0 critical messages.

FAIL: 0 error messages, expected 18.

PASS: 0 warning messages.

PASS: 0 notice messages.

FAIL: 0 info messages, expected more than 0.

FAIL: 0 debug messages, expected more than 0.

FAIL: 0 debug2 messages, expected more than 0.

FAIL: page_log formatted incorrectly.
access_log

error_log

page_log


I am a beginner to say the least when it comes to cups compiling, so at the moment I am clueless. For further references (maybe there's another way), here is the link to the normal manuals, look under "Printing, scanning and photocopying" for "printing through the internet":
[https://intranet.tudelft.nl/live/pagina.jsp?id=a25b9190-30ea-43a3-bca2-b0a468cf1e5f&lang=en]("https://intranet.tudelft.nl/live/pagina.jsp?id=a25b9190-30ea-43a3-bca2-b0a468cf1e5f&lang=en")

---

### Post by RudderDuck on 2010-09-08
Hi there,

For the Karmic netbook release I've made a page with detailed instructions, mostly taken from the page you're referring to, see: [http://serverconfig.wiki.xs4all.nl/index.php?title=Ubuntu_9.04_Netbook_Remix](http://serverconfig.wiki.xs4all.nl/index.php?title=Ubuntu_9.04_Netbook_Remix). This configuration does work for Delft uni, I work there and had it up and running until Lucid came along. I'm assuming you are using Lucid. Alas for Lucid I'm, like you, stuck with the 'dpkg-buildpackage -rfakeroot -uc -b' step. My guess is that some packages have changed names, for instance when issuing:

```

apt-get build-dep cupsys

```and

```
 apt-get source cupsys 
```I get this message:

Picking 'cups' as source package instead of 'cupsys'

I will have to look into this further and see where it goes wrong as it is rather silly that I'm unable to use the uni printers now :(

Hopefully someone with more knowledge of this can help us out.

---

### Post by HandleWithCare on 2010-09-09
It seems as if it should't all that difficult to get ssl support working, though I cannot find any guide that works for lucid like you.

---

### Post by edwinkcw on 2010-12-14
Hi, I face this problem also. Did you solve this already? I don't know how to use CUPS with SSL support :(

---

### Post by HandleWithCare on 2011-03-01
It has been a while, but for those still interested, I finally managed to get printing working at the TUDelft. It uses samba instead of ipp so I will not mark this thread solved just now.

The instruction on how to get printing via samba working can be found here:
[https://wiki.ubuntu.com/TUDelft-webprint]("https://wiki.ubuntu.com/TUDelft-webprint")

---

