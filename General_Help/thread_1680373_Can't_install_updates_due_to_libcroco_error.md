---
title: "Can't install updates due to libcroco error"
date: 2011-02-02
forum: General Help
---

### Post by shadowmane on 2011-02-02
I can't get my updates (or anything else) to install on my system.  I get this error from Update Manager.

```
installArchives() failed:  Extracting templates from packages: 28% Extracting templates from packages: 56% Extracting templates from packages: 84% Extracting templates from packages: 100% 
Preconfiguring packages ... 
 Extracting templates from packages: 28% Extracting templates from packages: 56% Extracting templates from packages: 84% Extracting templates from packages: 100% 
Preconfiguring packages ... 
dpkg: parse error, in file '/var/lib/dpkg/status' near line 29626 package 'libcroco3': 
 error in Version string 'online 
  - mailing-list-actions 
  - default-mailer 
  - email-custom-header 
  - import-ics-attachments 
  - prefer-plain 
  - mail-notification 
  - attachment-reminder 
  - backup-restore 
  - templates 
  - vcard-inline 
  - image-inline 
  - pst-import-1': version string has embedded spaces 

```When I look at /var/lib/dpkg/status in gedit for libcroco3 near line 29626 this is what I see.

```
Package: libcroco3
Status: deinstall ok installed
Priority: optional
Section: libs
Installed-Size: 296
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: libcroco
Version: nline
  - mailing-list-actions
  - default-mailer
  - email-custom-header
  - import-ics-attachments
  - prefer-plain
  - mail-notification
  - attachment-reminder
  - backup-restore
  - templates
  - vcard-inline
  - image-inline
  - pst-import-1
Depends: libc6 (>= 2.4), libglib2.0-0 (>= 2.16.0), libxml2 (>= 2.7.4)
Description: a generic Cascading Style Sheet (CSS) parsing and manipulation toolkit
 Services provided by Libcroco
  * A parser module that provides
    o A SAC like API. SAC stands for Simple API for CSS. SAC is an event driven
      API wich resembles SAX in the xml world.
    o A CSSOM like API. CSSOM stands for Cascading Style Sheet Object Model.
 .
    The libcroco parser implements the CSS Level 2 specification, the CSS
    forward compatibility rules and the CSS cascading rules.
 .
  * A CSS2 selection engine
    Given an xml element node (that obviously comes from an xml document) and
    a stylesheet cascade, the Libcroco selection engine can evaluate the css
    selectors of the cascade and return the style properties associated to
    the xml element node.
 .
    Note that the xml manipulation toolkit used by the libcroco selection
    engine at the moment is libxml2.
 .
 This package contains the shared libraries.
Original-Maintainer: Sebastien Bacher <seb128@debian.org>
```Can someone help me fix this?

---

### Post by shadowmane on 2011-02-03
Guess I have to bump this to the top.  Can anyone help me with this?

---

### Post by shadowmane on 2011-02-07
Is there nobody that can help me with this?

---

