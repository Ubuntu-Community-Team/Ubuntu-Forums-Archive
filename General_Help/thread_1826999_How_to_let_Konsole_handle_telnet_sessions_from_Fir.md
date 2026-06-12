---
title: "How to let Konsole handle telnet sessions from Firefox"
date: 2011-08-17
forum: General Help
---

### Post by subehsharma on 2011-08-17
Could somebody please tell me the script i can use to open telnet links from within Firefox using Konsole?

Think to note: I want to open every new Telnet link in a different tab of the Konsole window.

---

### Post by subehsharma on 2011-08-17
Bump!!!

---

### Post by subehsharma on 2011-08-17
create a shell scrip in /usr/bin/

#!/usr/bin/perl
# parse URL
($protocol,$host) = split /:\/\//, $ARGV[0];
($host,$port) = split /:/, $host;

# validate input
if ( $protocol !~ /^(telnet|ssh)$/ || $host !~ /^[a-zA-Z0-9.-]+$/ || $port !~ /(^[a-zA-Z0-9_-]+$|^$)/ ) {
        warn "Invalid URL";
        exit 1;
}

# if SSH, add -p argument
if ( $protocol eq "ssh" && $port != '' ) { $port = "-p $port" ; }

# call terminal emulator
exec("konsole --new-tab --hold -e $protocol $host $port");
exit;

---

