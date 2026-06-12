---
title: "Need a free US stock market software on Ubuntu"
date: 2010-03-06
forum: General Help
---

### Post by huangweiqiu on 2010-03-06
Please could anyone recommend a free stock (US) software on Ubuntu to me ? thanks

---

### Post by Johnny B on 2010-03-06
beancounter - A stock portfolio performance monitoring tool
qtstalker - commodity and stock market charting and technical analysis
smtm - Show Me The Money is a configurable Perl/Tk stock ticker program

---

### Post by yccheok on 2010-03-12
I would highly recommended you use [JStock - Free Stock Market Software]("http://jstock.sourceforge.net")

[IMG]http://2.bp.blogspot.com/_ttdgIQxreUA/S5OtWIIsyNI/AAAAAAAADPg/2SDsb4SxSQI/s400/jstock2-wording.png[/IMG]

---

### Post by stefcep on 2010-05-05
> **yccheok said:**
> I would highly recommended you use [JStock - Free Stock Market Software]("http://jstock.sourceforge.net")

[IMG]http://2.bp.blogspot.com/_ttdgIQxreUA/S5OtWIIsyNI/AAAAAAAADPg/2SDsb4SxSQI/s400/jstock2-wording.png[/IMG]

i downloaded jstock, extracted the archive, opened a shell, navigated to the extracted folder but there are no install instructions.  There is a jstock.sh file so in a terminal I typed sh jstock.sh.  I got "Warning: /bin/java does not exist".  I have installed java and updated it from synaptic.  jstock  needs Java to be in /bin, which it isn't.  Anyone know how I can install jstock?

BTW I have the windows version of jstock working with wine, but it makes the top menu bar disappear when it is running.

Ubuntu 9.04

---

### Post by yccheok on 2010-05-06
You need to specific JAVA_HOME.

If you open up the .sh file, you will see the following content :

```

#!/bin/bash
#
# Normally, editing this script should not be required.
# Only case is to set up JAVA_HOME if it's not already defined.
#
# To specify an alternative JVM, edit and uncomment the following 
# line and change the path accordingly.
#JAVA_HOME=/usr/lib/java

```

---

### Post by stefcep on 2010-05-07
> **yccheok said:**
> You need to specific JAVA_HOME.

If you open up the .sh file, you will see the following content :

```

#!/bin/bash
#
# Normally, editing this script should not be required.
# Only case is to set up JAVA_HOME if it's not already defined.
#
# To specify an alternative JVM, edit and uncomment the following 
# line and change the path accordingly.
#JAVA_HOME=/usr/lib/java

```

So what is the path to java in 9.04?  You'll have to dumb it down for me..

---

### Post by Red_Man on 2010-05-16
I am not sure about 9.04, but in 10.04 (Lucid) the path is /usr/share

The line in jstock.sh then becomes JAVA_HOME=/usr/share/java (delete the # at the start of the line)

The other thing that you might have to do is make the sh file executable (right click on the sh file icon in File Browser, left click on Properties then Permissions and then tick the executable box)

The program should now run if you double click its icon (in File Browser) and select Run.

Hope this helps

---

### Post by yccheok on 2011-02-10
_JStock 1.0.5x had been released, which has 6 features and 5 bugs fixed._

Feature: Stock Watchlist will able to load result saved from Stock Indicator Scanner.

Feature: Able to use left/right arrow key to move around yellow information boxes of Investment Flow Chart.

Feature: Make the stock purchase process smoother, by doesn't require user to press ENTER explicitly.

Feature: Automatic switch to the particular page, when user tries to activate a portfolio or watchlist.

Feature: Having a confirmation dialog box, to avoid user from clicking uninstall icon accidentally.

Feature: Indicator scanning completion progress will be displayed at status bar.

Bugfix: Able to suspend and resume network activity in PortfolioManagementJPanel when not in used, so that network resource is being preserved.

Bugfix: Adjust combo box popup width, so that horizontal scrollbar will not displayed.

Bugfix: Instead of limiting currency decimal places to 2 only, we allow them to float between 2 to 3, to avoid from losing precision.

Bugfix: Prevent user from uploading Stock Watchlist file with too many stocks to cloud server.

Bugfix: Under dividend dialog box, the stock selection through combo box will be sorted in alphabetical order.



You may download latest JStock 1.0.5x from [http://jstock.sourceforge.net/download.html]("http://jstock.sourceforge.net/download.html"). After upgrade, your personal data will be preserved.

**Please write us [Ratings and Reviews]("https://sourceforge.net/projects/jstock/reviews/") after you have used JStock, to help us in making JStock a better software.**

(We apologize for the delay of version 1.0.6, as there are quite a number of technical hurdles which prevent us from moving too fast.)

---

### Post by yccheok on 2011-03-29
_JStock 1.0.6 had been released, with 8 features and 5 bug fixes._

Feature: Supports stock merging and splitting. 

Feature: Supports stock buy and sell units in floating point. 

Feature: Investment flow chart able to show individual stock activity.

Feature: Able to restore previous position and size of JStock.

Feature: Easy way to add new stock which is not in offline database.

Feature: Able to choose between 1 or 2 columns stock input suggestion list.

Feature: We allow user to view history, even though offline database is not ready.

Bugfix: Portfolio page will be updated even though it is not being viewed.

Bugfix: Avoid empty record in dividend chart.

Bugfix: Change Italy stock index from S&P/MIB to FTSE MIB.

Bugfix: Able to delete multiple figures from indicator editor.

Bugfix: Remove splash screen for better simplicity user experience.

You may download latest JStock 1.0.6 from [http://jstock.sourceforge.net/download.html]("http://jstock.sourceforge.net/download.html"). After upgrade, your personal data will be preserved.

Please write us [Ratings and Reviews]("https://sourceforge.net/projects/jstock/reviews") after you have used JStock, to help us in making JStock a better software.

KLSE stock history is outdated for quite some time. We are still waiting fix from Yahoo! Here is [more information]("http://yccheok.blogspot.com/2011/03/klse-stock-history-outdated-for-yahoo.html") regarding this issue.

---

### Post by yccheok on 2012-04-04
JStock 1.0.6n had been released, with MACD added to Stock Indicator Editor.

Feature: Added MACD to Stock Relative History Information and Stock History Information. Please refer to [http://jstock.sourceforge.net/help_stock_indicator_editor.html#macd]("http://jstock.sourceforge.net/help_stock_indicator_editor.html#macd") for more information.

Bugfix: Spelling fix. Change "UnitedState" to "UnitedStates".

You may download latest JStock 1.0.6n from [http://jstock.sourceforge.net/download.html]("http://jstock.sourceforge.net/download.html"). After upgrade, your personal data will be preserved.

---

### Post by yccheok on 2012-11-18
**[SIZE="3"][A personal appeal]("http://jstock.sourceforge.net/personal-appeal.html") from JStock founder[/SIZE]**

**_JStock 1.0.6v had been released, with features and bugfix._**

Feature: Added Italian language. Contributed by Maurizio Da Lio.

Feature: Added "Refresh Stock Prices". Please refer to [http://jstock.sourceforge.net/help_real_time_info.html#scanning-speed]("http://jstock.sourceforge.net/help_real_time_info.html#scanning-speed")

Feature: UI cleanup, by removing unused buyer/seller information.
Bugfix: Bugfix on edit sell transaction. Buy cost should be adjusted after adjusting quantity.

You may download latest JStock 1.0.6v from [http://jstock.sourceforge.net/download.html]("http://jstock.sourceforge.net/download.html"). After upgrade, your personal data will be preserved.

---

### Post by wildmanne39 on 2012-11-18
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

