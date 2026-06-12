---
title: "Java installation issues"
date: 2009-11-06
forum: General Help
---

### Post by Butterknife on 2009-11-06
I've been notified by a website that I need to install Java. Fair enough, went to Java web, downloaded the .bin file and then got confused as to how to install it. I followed the instructions on Java web, used Nautilus to go to usr to create a java folder, opened root terminal and typed in what the website told me, but it didn't give me the result the instructions said it would. Here's what the terminal displays in the end:

```
root@Cortana:/home/ana# sudo mkdir /usr/java
root@Cortana:/home/ana# cd /usr/java/
root@Cortana:/usr/java# chmod a+x jre-6u<version>-linux-i586.bin
bash: version: No such file or directory
root@Cortana:/usr/java# jre-6u17-linux-i586-rpm.bin
jre-6u17-linux-i586-rpm.bin: command not found
root@Cortana:/usr/java# chmod a+x jre-6u17-linux-i586-rpm.bin
chmod: cannot access `jre-6u17-linux-i586-rpm.bin': No such file or directory
root@Cortana:/usr/java# sudo chown <ana> /usr/bin
bash: ana: No such file or directory
root@Cortana:/usr/java# chmod a+x jre-6u17-linux-i586-rpm.bin
root@Cortana:/usr/java# ls -l
total 19860
-rwxr-xr-x 1 root root 20334234 2009-11-06 08:01 jre-6u17-linux-i586-rpm.bin
root@Cortana:/usr/java# ./jre-6u17-linux-i586-rpm.bin
Sun Microsystems, Inc.  Binary Code License Agreement

for the JAVA SE RUNTIME ENVIRONMENT (JRE) VERSION 6 and
JAVAFX RUNTIME VERSION 1

SUN MICROSYSTEMS, INC.  ("SUN") IS WILLING TO LICENSE THE
SOFTWARE IDENTIFIED BELOW TO YOU ONLY UPON THE CONDITION
THAT YOU ACCEPT ALL OF THE TERMS CONTAINED IN THIS BINARY
CODE LICENSE AGREEMENT AND SUPPLEMENTAL LICENSE TERMS
(COLLECTIVELY "AGREEMENT"). PLEASE READ THE AGREEMENT
CAREFULLY.  BY USING THE SOFTWARE YOU ACKNOWLEDGE THAT 
YOU HAVE READ THE TERMS AND AGREE TO THEM. IF YOU ARE 
AGREEING TO THESE TERMS ON BEHALF OF A COMPANY OR OTHER 
LEGAL ENTITY, YOU REPRESENT THAT YOU HAVE THE LEGAL 
AUTHORITY TO BIND THE LEGAL ENTITY TO THESE TERMS. IF 
YOU DO NOT HAVE SUCH AUTHORITY, OR IF YOU DO NOT WISH 
TO BE BOUND BY THE TERMS, THEN YOU MUST NOT USE THE
SOFTWARE ON THIS SITE OR ANY OTHER MEDIA ON WHICH THE 
SOFTWARE IS CONTAINED.

1.  DEFINITIONS.  "Software" means the identified above in
binary form, any other machine readable materials
(including, but not limited to, libraries, source files,
header files, and data files), any updates or error
corrections provided by Sun, and any user manuals,
programming guides and other documentation provided to you
by Sun under this Agreement.  "General Purpose Desktop
Computers and Servers" means computers, including desktop
and laptop computers, or servers, used for general
computing functions under end user control (such as but not
specifically limited to email, general purpose Internet
browsing, and office suite productivity tools).  The use of
Software in systems and solutions that provide dedicated
functionality (other than as mentioned above) or designed
for use in embedded or function-specific software
applications, for example but not limited to: Software
embedded in or bundled with industrial control systems,
wireless mobile telephones, wireless handheld devices, 
netbooks, kiosks, TV/STB, Blu-ray Disc devices, telematics 
and network control switching equipment, printers and 
storage management systems, and other related systems are 
excluded from this definition and not licensed under this 
Agreement. "Programs" means (a) Java technology applets and
applications intended to run on the Java Platform Standard
Edition (Java SE) platform on Java-enabled General Purpose
Desktop Computers and Servers, and (b) JavaFX technology
applications intended to run on the JavaFX Runtime on
JavaFX-enabled General Purpose Desktop Computers and
Servers.

2.  LICENSE TO USE.  Subject to the terms and conditions of
this Agreement, including, but not limited to the Java
Technology Restrictions of the Supplemental License Terms,
Sun grants you a non-exclusive, non-transferable, limited
license without license fees to reproduce and use internally
Software complete and unmodified for the sole purpose of
running Programs.  Additional licenses for developers and/or
publishers are granted in the Supplemental License Terms.

3.  RESTRICTIONS.  Software is confidential and copyrighted.
Title to Software and all associated intellectual property
rights is retained by Sun and/or its licensors.  Unless
enforcement is prohibited by applicable law, you may not
modify, decompile, or reverse engineer Software.  You
acknowledge that Licensed Software is not designed or
intended for use in the design, construction, operation or
maintenance of any nuclear facility.  Sun Microsystems, Inc.
disclaims any express or implied warranty of fitness for
such uses.  No right, title or interest in or to any
trademark, service mark, logo or trade name of Sun or its
licensors is granted under this Agreement.  Additional
restrictions for developers and/or publishers licenses are
set forth in the Supplemental License Terms.

4.  LIMITED WARRANTY.  Sun warrants to you that for a period
of ninety (90) days from the date of purchase, as evidenced
by a copy of the receipt, the media on which Software is
furnished (if any) will be free of defects in materials and
workmanship under normal use.  Except for the foregoing,
Software is provided "AS IS".  Your exclusive remedy and
Sun's entire liability under this limited warranty will be
at Sun's option to replace Software media or refund the fee
paid for Software.  Any implied warranties on the Software
are limited to 90 days.  Some states do not allow
limitations on duration of an implied warranty, so the above
may not apply to you.  This limited warranty gives you
specific legal rights.  You may have others, which vary from
state to state.

5.  DISCLAIMER OF WARRANTY.  UNLESS SPECIFIED IN THIS
AGREEMENT, ALL EXPRESS OR IMPLIED CONDITIONS,
REPRESENTATIONS AND WARRANTIES, INCLUDING ANY IMPLIED
WARRANTY OF MERCHANTABILITY, FITNESS FOR A PARTICULAR
PURPOSE OR NON-INFRINGEMENT ARE DISCLAIMED, EXCEPT TO THE
EXTENT THAT THESE DISCLAIMERS ARE HELD TO BE LEGALLY
INVALID.

6.  LIMITATION OF LIABILITY.  TO THE EXTENT NOT PROHIBITED
BY LAW, IN NO EVENT WILL SUN OR ITS LICENSORS BE LIABLE FOR
ANY LOST REVENUE, PROFIT OR DATA, OR FOR SPECIAL, INDIRECT,
CONSEQUENTIAL, INCIDENTAL OR PUNITIVE DAMAGES, HOWEVER
CAUSED REGARDLESS OF THE THEORY OF LIABILITY, ARISING OUT OF
OR RELATED TO THE USE OF OR INABILITY TO USE SOFTWARE, EVEN
IF SUN HAS BEEN ADVISED OF THE POSSIBILITY OF SUCH DAMAGES.
In no event will Sun's liability to you, whether in
contract, tort (including negligence), or otherwise, exceed
the amount paid by you for Software under this Agreement.
The foregoing limitations will apply even if the above
stated warranty fails of its essential purpose.  Some states
do not allow the exclusion of incidental or consequential
damages, so some of the terms above may not be applicable to
you.

7.  TERMINATION.  This Agreement is effective until
terminated.  You may terminate this Agreement at any time by
destroying all copies of Software.  This Agreement will
terminate immediately without notice from Sun if you fail to
comply with any provision of this Agreement.  Either party
may terminate this Agreement immediately should any Software
become, or in either party's opinion be likely to become,
the subject of a claim of infringement of any intellectual
property right.  Upon Termination, you must destroy all
copies of Software.

8.  EXPORT REGULATIONS.  All Software and technical data
delivered under this Agreement are subject to US export
control laws and may be subject to export or import
regulations in other countries.  You agree to comply
strictly with all such laws and regulations and acknowledge
that you have the responsibility to obtain such licenses to
export, re-export, or import as may be required after
delivery to you.

9.  TRADEMARKS AND LOGOS.  You acknowledge and agree as
between you and Sun that Sun owns the SUN, SOLARIS, JAVA,
JINI, FORTE, and iPLANET trademarks and all SUN, SOLARIS,
JAVA, JINI, FORTE, and iPLANET-related trademarks, service
marks, logos and other brand designations ("Sun Marks"), and
you agree to comply with the Sun Trademark and Logo Usage
Requirements currently located at
http://www.sun.com/policies/trademarks.  Any use you make of
the Sun Marks inures to Sun's benefit.

10.  U.S.  GOVERNMENT RESTRICTED RIGHTS.  If Software is
being acquired by or on behalf of the U.S.  Government or by
a U.S.  Government prime contractor or subcontractor (at any
tier), then the Government's rights in Software and
accompanying documentation will be only as set forth in this
Agreement; this is in accordance with 48 CFR 227.7201
through 227.7202-4 (for Department of Defense (DOD)
acquisitions) and with 48 CFR 2.101 and 12.212 (for non-DOD
acquisitions).

11.  GOVERNING LAW.  Any action related to this Agreement
will be governed by California law and controlling U.S.
federal law.  No choice of law rules of any jurisdiction
will apply.

12.  SEVERABILITY.  If any provision of this Agreement is
held to be unenforceable, this Agreement will remain in
effect with the provision omitted, unless omission would
frustrate the intent of the parties, in which case this
Agreement will immediately terminate.

13.  INTEGRATION.  This Agreement is the entire agreement
between you and Sun relating to its subject matter.  It
supersedes all prior or contemporaneous oral or written
communications, proposals, representations and warranties
and prevails over any conflicting or additional terms of any
quote, order, acknowledgment, or other communication between
the parties relating to its subject matter during the term
of this Agreement.  No modification of this Agreement will
be binding, unless in writing and signed by an authorized
representative of each party.

SUPPLEMENTAL LICENSE TERMS

These Supplemental License Terms add to or modify the terms
of the Binary Code License Agreement.  Capitalized terms not
defined in these Supplemental Terms shall have the same
meanings ascribed to them in the Binary Code License
Agreement .  These Supplemental Terms shall supersede any
inconsistent or conflicting terms in the Binary Code License
Agreement, or in any license contained within the Software.

A.  Software Internal Use and Development License Grant.
Subject to the terms and conditions of this Agreement and
restrictions and exceptions set forth in the Software
"README" file incorporated herein by reference, including,
but not limited to the Java Technology Restrictions of these
Supplemental Terms, Sun grants you a non-exclusive,
non-transferable, limited license without fees to reproduce
internally and use internally the Software complete and
unmodified for the purpose of designing, developing, and
testing your Programs.

B.  License to Distribute Software.  Subject to the terms
and conditions of this Agreement and restrictions and
exceptions set forth in the Software README file, including,
but not limited to the Java Technology Restrictions of these
Supplemental Terms, Sun grants you a non-exclusive,
non-transferable, limited license without fees to reproduce
and distribute the Software (except for the JavaFX Runtime),
provided that (i) you distribute the Software complete and
unmodified and only bundled as part of, and for the sole
purpose of running, your Programs, (ii) the Programs add
significant and primary functionality to the Software, (iii)
you do not distribute additional software intended to
replace any component(s) of the Software, (iv) you do not
remove or alter any proprietary legends or notices contained
in the Software, (v) you only distribute the Software
subject to a license agreement that protects Sun's interests
consistent with the terms contained in this Agreement, and
(vi) you agree to defend and indemnify Sun and its licensors
from and against any damages, costs, liabilities, settlement
amounts and/or expenses (including attorneys' fees) incurred
in connection with any claim, lawsuit or action by any third
party that arises or results from the use or distribution of
any and all Programs and/or Software.

C.  Java Technology Restrictions.  You may not create,
modify, or change the behavior of, or authorize your
licensees to create, modify, or change the behavior of,
classes, interfaces, or subpackages that are in any way
identified as "java", "javax", "sun" or similar convention
as specified by Sun in any naming convention designation.

D.  Source Code.  Software may contain source code that,
unless expressly licensed for other purposes, is provided
solely for reference purposes pursuant to the terms of this
Agreement.  Source code may not be redistributed unless
expressly provided for in this Agreement.

E.  Third Party Code.  Additional copyright notices and
license terms applicable to portions of the Software are set
forth in the THIRDPARTYLICENSEREADME.txt file.  In addition
to any terms and conditions of any third party
opensource/freeware license identified in the
THIRDPARTYLICENSEREADME.txt file, the disclaimer of warranty
and limitation of liability provisions in paragraphs 5 and 6
of the Binary Code License Agreement shall apply to all
Software in this distribution.

F.  Termination for Infringement.  Either party may
terminate this Agreement immediately should any Software
become, or in either party's opinion be likely to become,
the subject of a claim of infringement of any intellectual
property right.

G.  Installation and Auto-Update.  The Software's
installation and auto-update processes transmit a limited
amount of data to Sun (or its service provider) about those
specific processes to help Sun understand and optimize them.
Sun does not associate the data with personally identifiable
information.  You can find more information about the data
Sun collects at http://java.com/data/.

For inquiries please contact: Sun Microsystems, Inc., 4150
Network Circle, Santa Clara, California 95054, U.S.A.



Do you agree to the above license terms? [yes or no]
yes
Unpacking...
Checksumming...
Extracting...
UnZipSFX 5.50 of 17 February 2002, by Info-ZIP (Zip-Bugs@lists.wku.edu).
  inflating: jre-6u17-linux-i586.rpm  
./jre-6u17-linux-i586-rpm.bin: 440: rpm: not found
 
Done.
root@Cortana:/usr/java# rpm -iv jre-6u17-linux-i586-rpm.bin
The program 'rpm' is currently not installed.  You can install it by typing:
apt-get install rpm
rpm: command not found
root@Cortana:/usr/java# 

```I used the apt-get to install "rpm", after which this is the message I'm getting:

```
root@Cortana:/usr/java# rpm -iv jre-6u17-linux-i586-rpm
rpm: please use alien to install rpm packages on Debian, if you are really sure use --force-debian switch. See README.Debian for more details.
root@Cortana:/usr/java# 

```I know I'm doing something wrong, but being a beginner, I don't know what, so any help is appreciated.

---

### Post by albandy on 2009-11-06
You have java in the repositories.

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

---

### Post by konqueror7 on 2009-11-06
follow albandy's method and you will be fine,,, the reason also that your java is not installing is because you downloaded a different version, you must have downloaded the plain one ending with '*-linux.bin'...ubuntu uses the *deb format, yo you cannot use *.rpm here...

---

### Post by Butterknife on 2009-11-06
I see, done and done, thanks for the help. I find it odd that Sun web doesn't offer a .deb package, they all ended in .bin so I chose one of the two 32-bit offered..

---

### Post by scouser73 on 2009-11-06
I've found this to be a great tutorial for installing Sun Java: [[COLOR="Red"]**Ubuntu Install Sun Java**[/COLOR]]("http://sites.google.com/site/easylinuxtipsproject/java")

---

### Post by Butterknife on 2009-11-06
Ah! See, that tutorial wants the .bin file from Sun website. Quite an amount of contradiction around. Should I uninstall the version I got through repositories and follow the tutorial?

---

### Post by scouser73 on 2009-11-06
Yes, it's very easy to use, it does state that this is for Ubuntu 9.10 only but I've done it on Ubuntu 9.04 and it works perfectly.

---

### Post by Mighty_Joe on 2009-11-06
Personally, I rely on the repositories.  Then the update manager informs me of updates and the installer takes care of configuring the system to use the new release.  
If you install Java using the tutorial scouser73 posted, you'll have to keep an eye out for Java updates, install them and configure the system to use them yourself. 
FYI, according to scouser73's link, Sun Java is not going to be updated anymore and we're supposed to use OpenJDK (the open-source version of Sun's JDK).  It's in the repos as well.

---

### Post by Sef on 2009-11-06
> Ah! See, that tutorial wants the .bin file from Sun website. Quite an amount of contradiction around. Should I uninstall the version I got through repositories and follow the tutorial?

I would uninstall anything you installed then download Java from Ubuntu's repositories.

---

