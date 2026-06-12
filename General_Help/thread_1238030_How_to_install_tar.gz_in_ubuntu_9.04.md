---
title: "How to install tar.gz in ubuntu 9.04"
date: 2009-08-12
forum: General Help
---

### Post by karthick87 on 2009-08-12
I want to install squid-graph in my PC,I have downloaded the file but it is in tar.gz format..Since i am new to linux,can you some help me to install this..?

---

### Post by Tclarkie on 2009-08-12
try this [COLOR=#008000]linux.com/archive/forums/topic/4465[/COLOR]

---

### Post by gardara on 2009-08-12
> Installation:

Extracting the Tarball

· Extract the Squid Graph tarball file after you have downloaded it. Those with Redhat Linux (or other similar distributions) can do this: -

$ tar -zxvf squid-graph-x.x.tar.gz

· Alternatively, those with UNIX-like operating systems can do this: -

$ zcat squid-graph-x.x.tar.gz | tar -xvf -

Gathering the Pre-requisites

· As of version 3.0, Squid Graph requires the GD perl module. You can download it from [http://stein.cshl.org/WWW/software/GD/](http://stein.cshl.org/WWW/software/GD/) or you can use the included GD-1.3.3.tar.gz file in the extras/ directory.

· Follow the intructions in the GD perl module to get it installed correctly before you proceed.

Compiling

· Squid Graph runs out of the box. You don't have to compile it.

Putting it in the Right Place

· You might not prefer to have Squid Graph lying around in your current directory, so you should just move it to a directory which makes sense, such as /usr/local/squid-graph. e.g.

$ mv squid-graph-x.x /usr/local/squid-graph



Runing Squid Graph:

Quickstart

First, get yourself into the bin/ directory, for example: -

$ cd /usr/local/squid-graph/bin

Next, you run Squid Graph with the default options. The bare minimum for Squid Graph to run is the --output-dir option. The output directory is where the generated HTML reports and image files would be written.

$ ./squid-graph --output-dir=/var/www/html/reports < /usr/local/squid/logs/access.log

NOTE: Please check your directory permissions of your output directory!

Usually you would want the output to be generated into a directory which your web server is configured with access to. In the above example, /usr/local/squid/logs/access.log is your Squid logfile.

Where you store your Squid logfile differs from system to system. For default Redhat Linux installations, it should be in /log/squid/access.log. For those who compiled and installed Squid with the default options, it should be in /usr/local/squid/logs/access.log.

Removing the TCP or UDP Graphs

Most of you won't use cache ICP or log cache ICP, so there won't be any UDP messages in your logfiles. Disabling UDP is a good idea. You can do this by specifying the --tcp-only command line option.

$ ./squid-graph --tcp-only --output-dir=/var/www/re...

Likewise, if you only want to see UDP statistics, you can specify the --udp-only option.

$ ./squid-graph --udp-only --output-dir=/var/www/re...

Generating Cumulative Graphs

As of version 3.0, Squid Graph comes with a new feature to generage cumulative curves instead of the normal graphs. This can be done by specifying the --cumulative option.

$ ./squid-graph --cumulative --tcp-only --output-dir=/var/www/re...

To have a better understanding of what cumulative curves are, take a look at the output examples. Do note that enabling cumulative graphs disables the Average Transfer Duration graph automatically.

Disabling Average Transfer Duration Graphs

You can disable the Average Transfer Duration Graph by specifying the --no-transfer-duration option.

$ ./squid-graph --no-transfer-duration --output-dir=/var/www/re...

Specifying the Start/End Time

By default, Squid Graph generates reports based on the current time. It starts analyzing from 24 hours before the current time until the current time. Sometimes we cycle logfiles so it is necessary to specify when you want Squid Graph to start looking at your log files. This is done by specifying the --start option.

$ ./squid-graph --start=991353612 --output-dir=/var/www/re...

Likewise, you can specify the end time and Squid will automatically calculate the start time for you. This is done by specifying the --end command line option.

$ ./squid-graph --end=991352122 --output-dir=/var/www/re...

To get the last line of the Squid logfile, simply use tail -n1 logfile.log

Note that the start value is a numerical value which represents the number of seconds since 1970, NOT the conventional hh:mm:ss dd/mm/yyyy format. The reason why we did this is because Squid logs its time in this format, and we can easily use head -n1 logfile.log to view the first line of the log file to determine the start time


Taken from: [http://linux.softpedia.com/get/Internet/Log-Analyzers/Squid-Graph-1356.shtml](http://linux.softpedia.com/get/Internet/Log-Analyzers/Squid-Graph-1356.shtml)

---

### Post by karthick87 on 2009-08-12
I cant install the GD Perl Module,this is my output...
karthick@karthick:~/Desktop/GD-2.44$  perl Makefile.PL
Notice: Type perl Makefile.PL -h for command-line option summary.

**UNRECOVERABLE ERROR**
Could not find gdlib-config in the search path. Please install libgd 2.0.28 or higher.
If you want to try to compile anyway, please rerun this script with the option --ignore_missing_gd.

---

### Post by Soul-Sing on 2009-08-12
Is squidview an option? It is in the repos.of ubuntu.

---

### Post by harry2006 on 2009-08-12
> **getyourkarthick said:**
> I cant install the GD Perl Module,this is my output...
karthick@karthick:~/Desktop/GD-2.44$  perl Makefile.PL
Notice: Type perl Makefile.PL -h for command-line option summary.

**UNRECOVERABLE ERROR**
Could not find gdlib-config in the search path. Please install libgd 2.0.28 or higher.
If you want to try to compile anyway, please rerun this script with the option --ignore_missing_gd.
i think the error message points to some config issue...

---

### Post by karthick87 on 2009-08-12
Do i want to install any additional package??

---

