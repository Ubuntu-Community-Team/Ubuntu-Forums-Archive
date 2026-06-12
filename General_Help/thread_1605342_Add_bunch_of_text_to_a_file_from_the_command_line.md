---
title: "Add bunch of text to a file from the command line"
date: 2010-10-25
forum: General Help
---

### Post by inameiname on 2010-10-25
I'm curious if there is a way to add a bunch of lines of text to a text file. I'm asking more than the usual:

```

echo 'whatever I want to put on this line #1' >> Textfile.txt
echo 'whatever I want to put on this line #2' >> Textfile.txt
echo 'whatever I want to put on this line #3' >> Textfile.txt
echo 'whatever I want to put on this line #4' >> Textfile.txt
echo 'whatever I want to put on this line #20007' >> Textfile.txt

```Basically, my issue with doing the above is that if I have special characters within the single quotes, there is an error. Plain text with just words and little punctuation works. It's a shame I just can't copy an entire page of text (with many lines) and somehow put that within the parameters of an 'echo' command.

I know it's already possible to add an entire text file into another, but that's not what I'm asking, as my question is in regards to a script I'm making, in which I want to add a bunch of lines in it, such as those above, so they will auto-add lines of text to the 'Textfile.txt' I want.

---

### Post by cannywizard on 2010-10-25
You can usually escape special characters with a backslash before them, but I'm not sure that's what you want. Do you have a specific example?

---

### Post by DaithiF on 2010-10-25
sounds like you want a 'here document'. eg.

```
cat <<EOF >> somefile
first line!
second line...
# third line
etc
etc, blah blah
EOF

```

---

### Post by DaithiF on 2010-10-25
and just to note, add quotes around the delimiter word to suppress bash expansion of variables, command substitution etc.
cat <<"EOF" > somefile

**man bash**, and search for 'Here Documents' for more info

---

### Post by inameiname on 2010-10-25
Okay, cannywizard, here is an example. I want to add ALL of these lines to a text file (they make up a text file already, but it won't be installed/I want to copy all of these onto a current one) by having these lines inside a script:

```

# Sample configuration file for Polipo. -*-sh-*-

# You should not need to edit this configuration file; all configuration
# variables have reasonable defaults.

# This file only contains some of the configuration variables; see the
# list given by ``polipo -v'' and the manual for more.


### Basic configuration
### *******************

# Uncomment one of these if you want to allow remote clients to
# connect:

# proxyAddress = "::0"        # both IPv4 and IPv6
# proxyAddress = "0.0.0.0"    # IPv4 only

# If you are enabling 'proxyAddress' above, then you want to enable the
# 'allowedClients' variable to the address of your network, e.g.
# allowedClients = 127.0.0.1, 192.168.42.0/24

# allowedClients = 127.0.0.1

# Uncomment this if you want your Polipo to identify itself by
# something else than the host name:

# proxyName = "polipo.example.org"

# Uncomment this if there's only one user using this instance of Polipo:

# cacheIsShared = false

# Uncomment this if you want to use a parent proxy:

# parentProxy = "squid.example.org:3128"

# Uncomment this if you want to use a parent SOCKS proxy:

# socksParentProxy = "localhost:9050"
# socksProxyType = socks5


### Memory
### ******

# Uncomment this if you want Polipo to use a ridiculously small amount
# of memory (a hundred C-64 worth or so):

# chunkHighMark = 819200
# objectHighMark = 128

# Uncomment this if you've got plenty of memory:

# chunkHighMark = 50331648
# objectHighMark = 16384


### On-disk data
### ************

# Uncomment this if you want to disable the on-disk cache:

# diskCacheRoot = ""

# Uncomment this if you want to put the on-disk cache in a
# non-standard location:

# diskCacheRoot = "~/.polipo-cache/"

# Uncomment this if you want to disable the local web server:

# localDocumentRoot = ""

# Uncomment this if you want to enable the pages under /polipo/index?
# and /polipo/servers?.  This is a serious privacy leak if your proxy
# is shared.

# disableIndexing = false
# disableServersList = false


### Domain Name System
### ******************

# Uncomment this if you want to contact IPv4 hosts only (and make DNS
# queries somewhat faster):

# dnsQueryIPv6 = no

# Uncomment this if you want Polipo to prefer IPv4 to IPv6 for
# double-stack hosts:

# dnsQueryIPv6 = reluctantly

# Uncomment this to disable Polipo's DNS resolver and use the system's
# default resolver instead.  If you do that, Polipo will freeze during
# every DNS query:

# dnsUseGethostbyname = yes


### HTTP
### ****

# Uncomment this if you want to enable detection of proxy loops.
# This will cause your hostname (or whatever you put into proxyName
# above) to be included in every request:

# disableVia=false

# Uncomment this if you want to slightly reduce the amount of
# information that you leak about yourself:

# censoredHeaders = from, accept-language
# censorReferer = maybe

# Uncomment this if you're paranoid.  This will break a lot of sites,
# though:

# censoredHeaders = set-cookie, cookie, cookie2, from, accept-language
# censorReferer = true

# Uncomment this if you want to use Poor Man's Multiplexing; increase
# the sizes if you're on a fast line.  They should each amount to a few
# seconds' worth of transfer; if pmmSize is small, you'll want
# pmmFirstSize to be larger.

# Note that PMM is somewhat unreliable.

# pmmFirstSize = 16384
# pmmSize = 8192

# Uncomment this if your user-agent does something reasonable with
# Warning headers (most don't):

# relaxTransparency = maybe

# Uncomment this if you never want to revalidate instances for which
# data is available (this is not a good idea):

# relaxTransparency = yes

# Uncomment this if you have no network:

# proxyOffline = yes

# Uncomment this if you want to avoid revalidating instances with a
# Vary header (this is not a good idea):

# mindlesslyCacheVary = true

# Suggestions from Incognito configuration
maxConnectionAge = 5m
maxConnectionRequests = 120
serverMaxSlots = 8
serverSlots = 2
tunnelAllowedPorts = 1-65535

```Looking at this example, I could technically go through each and every line of text and add:

```

sudo sh -c "echo 'LINE1' > /etc/polipo/config"
sudo sh -c "echo 'LINE2' >> /etc/polipo/config"
sudo sh -c "echo 'LINE3' >> /etc/polipo/config"

```...cleaning up "LINE1", "LINE2", "LINE3", etc using backslashes for all the special characters, (which is want I want, but would take an insane amount of time to weed out).

A simpler way would be nice because this isn't the only text I want to copy to a text file using a script.



To DaithiF:

Okay, so I'm trying to grasp the idea of a 'Here Document.' How might I apply that to say the text above?




In all, I want EXACTLY all of those lines (including the spaces) to be added to a text file, so when I'm done, it looks just like I would have 'cp' it from a text file to a text file.

---

### Post by cannywizard on 2010-10-25
It's possible to do a 'find-replace' for the special characters and escape them automatically. I did this a while ago. The section of my (perl) script looks like this. Perhaps you can adapt it for what you need. sed should work similarly if you're using bash.

```

    # these escape some special characters
    
    $fname =~ s/ /\\ /g; # space
    
    $fname =~ s/&/\\&/g; # ampersand
    
    $fname =~ s/\(/\\\(/g; # open paren
    
    $fname =~ s/\)/\\\)/g; # close paren

    $fname =~ s/\+/\\\+/g; # plus
    
    $fname =~ s/\>/\\\>/g; # greater than

    $fname =~ s/\</\\\</g; # less than

    # do stuff with fname
```
Perhaps there's a way to combine all of those into one command.

---

### Post by inameiname on 2010-10-25
I just found this little bit of info, which I think leads me on the right track:

```

   1 #!/bin/bash
   2 
   3 #  'echo' is fine for printing single line messages,
   4 #+  but somewhat problematic for for message blocks.
   5 #   A 'cat' here document overcomes this limitation.
   6 
   7 cat <<End-of-message
   8 -------------------------------------
   9 This is line 1 of the message.
  10 This is line 2 of the message.
  11 This is line 3 of the message.
  12 This is line 4 of the message.
  13 This is the last line of the message.
  14 -------------------------------------
  15 End-of-message
  16 
  17 #  Replacing line 7, above, with
  18 #+   cat > $Newfile <<End-of-message
  19 #+       ^^^^^^^^^^
  20 #+ writes the output to the file $Newfile, rather than to stdout.
  21 
  22 exit 0

```

Seems then, that if I were to:

```

Newfile="/etc/polipo/config"
cat > $Newfile <<End-of-message
MY_TEXT_FILE_ABOVE
<<End-of-message

```

---

### Post by inameiname on 2010-10-25
Oh thanks, cannywizard. That is what I did before, using 'search and replace', but never seemed to get it right. The inputs you gave though might make it much easier. Regardless, they will definitely be handy for later need. 

Anyway, I think if this "Here Document" thing works the way I'm hoping it does, it'd be even easier.

---

### Post by DaithiF on 2010-10-25
> **inameiname said:**
> Seems then, that if I were to:

```

Newfile="/etc/polipo/config"
cat > $Newfile <<**"**End-of-message**"**
MY_TEXT_FILE_ABOVE
<<End-of-message

```

yes, just add quotes around your end of message marker as above, in case you have any special chars in the body of the text that bash might otherwise try to expand

Edit:  don't include the << on the last line, just End-of-message

---

### Post by inameiname on 2010-10-25
PERFECT!!!!! EXCEPT FOR ONE THING:

```

<<End-of-message

```

That last line is actually in the file "/etc/polipo/config"


Is there a way to remove that one?

As a workaround, if I MUST have something there, would a "#" work, as it wouldn't mess anything up in any text file?

---

### Post by inameiname on 2010-10-25
Nevermind. I did not notice:

```

Edit:  don't include the << on the last line, just End-of-message

```It works the way I want. 

Thank you both for your suggestions. I'll mark this as solved.

---

