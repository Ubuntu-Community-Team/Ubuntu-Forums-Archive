---
title: "Bugzilla 3.4.3 -Perl Modules installation"
date: 2009-11-13
forum: General Help
---

### Post by mithun.kamath on 2009-11-13
Hi,

I am trying to install Bugzilla 3.4.3 in Ubuntu 9.04- the Jaunty Jackalope. To certain Step of procedure of installation it was smooth.When it came to the perl module installation, its pulling me down. Some of the perl modules that are essential, i am not able to install.

This is what i tried

```
kamath@kamath-desktop:/$ cd '/usr/local/bugzilla-3.4.3' 
kamath@kamath-desktop:/usr/local/bugzilla-3.4.3$ '/usr/local/bugzilla-3.4.3/checksetup.pl' 
* This is Bugzilla 3.4.3 on perl 5.10.0
* Running on Linux 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009

Checking perl modules...
Checking for              CGI.pm (v3.33)   ok: found v3.48 
Checking for          Digest-SHA (any)     ok: found v5.45 
Checking for            TimeDate (v2.21)   ok: found v2.22 
Checking for            DateTime (v0.28)    not found 
Checking for   DateTime-TimeZone (v0.71)    not found 
Checking for                 DBI (v1.41)   ok: found v1.607 
Checking for    Template-Toolkit (v2.22)   ok: found v2.22 
Checking for          Email-Send (v2.00)   ok: found v2.198 
Checking for          Email-MIME (v1.861)  ok: found v1.902 
Checking for Email-MIME-Encodings (v1.313)  ok: found v1.313 
Checking for Email-MIME-Modifier (v1.442)  ok: found v1.902 
Checking for                 URI (any)     ok: found v1.37 

Checking available perl DBD modules...
Checking for              DBD-Pg (v1.45)    not found 
Checking for           DBD-mysql (v4.00)   ok: found v4.008 
Checking for          DBD-Oracle (v1.19)    not found 

The following Perl modules are optional:
Checking for                  GD (v1.20)    not found 
Checking for               Chart (v1.0)     not found 
Checking for         Template-GD (any)      not found 
Checking for          GDTextUtil (any)      not found 
Checking for             GDGraph (any)      not found 
Checking for            XML-Twig (any)     ok: found v3.32 
Checking for          MIME-tools (v5.406)  ok: found v5.427 
Checking for         libwww-perl (any)     ok: found v5.819 
Checking for         PatchReader (v0.9.4)  ok: found v0.9.5 
Checking for          PerlMagick (any)      not found 
Checking for           perl-ldap (any)     ok: found v0.39 
Checking for         Authen-SASL (any)     ok: found v2.13 
Checking for          RadiusPerl (any)     ok: found v0.15 
Checking for           SOAP-Lite (v0.710.06) ok: found v0.710.10 
Checking for         HTML-Parser (v3.40)   ok: found v3.59 
Checking for       HTML-Scrubber (any)     ok: found v0.08 
Checking for Email-MIME-Attachment-Stripper (any)     ok: found v1.316 
Checking for         Email-Reply (any)     ok: found v1.202 
Checking for         TheSchwartz (any)      not found 
Checking for      Daemon-Generic (any)     ok: found v0.61 
Checking for            mod_perl (v1.999022)  not found 
***********************************************************************
* REQUIRED MODULES                                                    *
***********************************************************************
* Bugzilla requires you to install some Perl modules which are either *
* missing from your system, or the version on your system is too old. *
* See below for commands to install these modules.                    *
***********************************************************************
* OPTIONAL MODULES                                                    *
***********************************************************************
* Certain Perl modules are not required by Bugzilla, but by           *
* installing the latest version you gain access to additional         *
* features.                                                           *
*                                                                     *
* The optional modules you do not have installed are listed below,    *
* with the name of the feature they enable. Below that table are the  *
* commands to install each module.                                    *
***********************************************************************
* MODULE NAME * ENABLES FEATURE(S)                                    *
***********************************************************************
*          GD * Graphical Reports, New Charts, Old Charts             *
*       Chart * New Charts, Old Charts                                *
* Template-GD * Graphical Reports                                     *
*  GDTextUtil * Graphical Reports                                     *
*     GDGraph * Graphical Reports                                     *
*  PerlMagick * Optionally Convert BMP Attachments to PNGs            *
* TheSchwartz * Mail Queueing                                         *
*    mod_perl * mod_perl                                              *
***********************************************************************
COMMANDS TO INSTALL OPTIONAL MODULES:

             GD: /usr/bin/perl install-module.pl GD
          Chart: /usr/bin/perl install-module.pl Chart::Base
    Template-GD: /usr/bin/perl install-module.pl Template::Plugin::GD::Image
     GDTextUtil: /usr/bin/perl install-module.pl GD::Text
        GDGraph: /usr/bin/perl install-module.pl GD::Graph
     PerlMagick: /usr/bin/perl install-module.pl Image::Magick
    TheSchwartz: /usr/bin/perl install-module.pl TheSchwartz
       mod_perl: /usr/bin/perl install-module.pl mod_perl2

COMMANDS TO INSTALL REQUIRED MODULES (You *must* run all these commands
and then re-run checksetup.pl):

    /usr/bin/perl install-module.pl DateTime
    /usr/bin/perl install-module.pl DateTime::TimeZone

To attempt an automatic install of every required and optional module
with one command, do:

  /usr/bin/perl install-module.pl --all

kamath@kamath-desktop:/usr/local/bugzilla-3.4.3$ 

```

I tried all the commands in the above section, but still says modules not found.

Please help me

Thanks,
Mithun Kamath

---

### Post by mithun.kamath on 2009-11-14
has any one tried installing bugzilla in 9.04

---

### Post by mithun.kamath on 2009-11-17
OK, here some update.

I was getting error after error. Finaly I decided to Post to bugzilla mailing list. And here is what i got the reply


Message: 2
Date: Sun, 15 Nov 2009 14:05:52 -0800 (PST)
To: [email]support-bugzilla@lists.mozilla.org[/email]
Subject: Re: Bugzilla 3.4.3 -Perl Modules installation
Message-ID:
    <69b73be2-e767-4940-9659-e7e24e898732@j4g2000yqe.googlegroups.com>
Content-Type: text/plain; charset=ISO-8859-1

On 14 Lis, 10:02, kamath <mithunkam...@ymail.com> wrote:
> COMMANDS TO INSTALL REQUIRED MODULES (You *must* run all these commands
> and then re-run checksetup.pl):

Hi.
You can try:
***apt-get install libdatetime-perl***

and it worked!!!!!!!!!!


------------------------------

---

