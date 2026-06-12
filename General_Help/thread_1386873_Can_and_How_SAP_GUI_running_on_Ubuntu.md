---
title: "Can and How SAP GUI running on Ubuntu?"
date: 2010-01-21
forum: General Help
---

### Post by xiaoqi on 2010-01-21
Hello all,

I'm involving in one client environment migration project, which aiming migrate existing enterprise Windows based client to Ubuntu open source client.

During the research, most of the software / applications can be migrated from "close source" to Open Source, e.g.
[LIST]
[*]Microsoft Office --> Open Office
[*]Internet Explorer --> Firefox
[*]Microsoft Project --> GANTT
[*]Live Meeting --> DimDim
[*]Photoshop --> GIMP
[*]Micro$oft Outlook --> Revolution
[/LIST]

But today we're facing challenge to cope with later SAP ERP application, checked with several source, seems SAP does not be friendly to Ubuntu, although they declare that they're comparible with RedHat, but never see formal statement that SAP is compliance with Ubuntu.

Does anyone here in expertise give some help to me on this understanding?

1. Whether we can say that we can run SAP GUI (seems must be JAVA edition) on Ubuntu e.g. 9.10, 10.04 later?
and
2. If can, shall anyone share some experience of configuration steps for this? What customization must be done in either Ubuntu client side, or SAP server side?

This is very critical dependency, so would like to see any experiences.

Thanks.

---

### Post by falconindy on 2010-01-21
Java is, for the most part, OS agnostic. If the SAP GUI works with RedHat, it should work with Ubuntu. Have you tried it yet? Are there any errors that prevent it from running?

---

### Post by tooCanad on 2010-07-25
> **xiaoqi said:**
> Hello all,

I'm involving in one client environment migration project, which aiming migrate existing enterprise Windows based client to Ubuntu open source client.

During the research, most of the software / applications can be migrated from "close source" to Open Source, e.g.
[LIST]
[*]Microsoft Office --> Open Office
[*]Internet Explorer --> Firefox
[*]Microsoft Project --> GANTT
[*]Live Meeting --> DimDim
[*]Photoshop --> GIMP
[*]Micro$oft Outlook --> Revolution
[/LIST]

But today we're facing challenge to cope with later SAP ERP application, checked with several source, seems SAP does not be friendly to Ubuntu, although they declare that they're comparible with RedHat, but never see formal statement that SAP is compliance with Ubuntu.

Does anyone here in expertise give some help to me on this understanding?

1. Whether we can say that we can run SAP GUI (seems must be JAVA edition) on Ubuntu e.g. 9.10, 10.04 later?
and
2. If can, shall anyone share some experience of configuration steps for this? What customization must be done in either Ubuntu client side, or SAP server side?

This is very critical dependency, so would like to see any experiences.

Thanks.

I've been running the java client on an ubuntu work station for the past three years. No issues. The is also web gui which should run in firefox.

---

