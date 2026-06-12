---
title: "Libreoffice Base toolbars not showing up, slow, report crashes LO"
date: 2012-01-02
forum: General Help
---

### Post by notbitmonk on 2012-01-02
I was a MS Access hobbyist in my Microsoft years. I learned to build databases to cover many needs for our small office. I changed to Ubuntu full time, at home, about 4 years ago. I stopped database development and just started again as I needed some function that I know a database can provide. I have 10.04 with the LibreOffice PPA. Created some tables and there were some differences but that is all part of the learning experience. Going to the forms I started just like I did with Access, with the wizards. The form got created. I noticed some things that I wanted to change so I opened up the form in design mode. Again, some problems selecting items (CTRL-click to select individual items) that were part of the learning curve (see chapter 8 of the OpenOffice Getting Started Guide). At this point is where the problem arose. The toolbars are not showing up. I went to View --> Toolbars to select the form toolbars and nothing happens after I click on them. Opening tables show the total record count at the bottom but the number is wrong. I have a table with 129 records. The record count showed only 16. I had to navigate to the last record to have the correct number show up. This was a slow operation too. I went then to prepare a simple report to see if the problem of the toolbar and speed showed up. Tried the wizard which went good until it tried to show the report. It threw an error. Then I tried the manual report creation which went really good. Until I tried to run the report. This time, it crashed the application.
At this point, I do not know if this is a bug for the LibreOffice team or the Ubuntu team. I have used Calc, Writer, Impress, Draw and Math without problems which to me seems to rule out the possibility of problem on my end. I am thinking of unistalling LibreOffice and installing the deb from the LibreOffice website.
Report error information that crashes Base:
```
SQL Status: S1000
An error occurred while creating the report.
An exception of type com.sun.star.uno.RuntimeException was caught.
[jni_uno bridge error] UNO calling Java method execute: non-UNO exception occurred: java.lang.NoClassDefFoundError: Could not initialize class com.sun.star.report.SDBCReportDataFactory
java stack trace:
java.lang.NoClassDefFoundError: Could not initialize class com.sun.star.report.SDBCReportDataFactory
	at com.sun.star.report.pentaho.SOReportJobFactory$_SOReportJobFactory.createReportJob(SOReportJobFactory.java:322)
	at com.sun.star.report.pentaho.SOReportJobFactory$_SOReportJobFactory.execute(SOReportJobFactory.java:222)

```
LibreOffice version
```
LibreOffice 3.3.2 
OOO330m19 (Build:202)
tag libreoffice-3.3.2.2, Ubuntu package 1:3.3.2-1ubuntu2~lucid1
```
Java
```
Sun Microsystems, Inc. version 1.6.0_20
```

---

### Post by notbitmonk on 2012-01-06
Reported as a bug.
[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/912734](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/912734)

---

