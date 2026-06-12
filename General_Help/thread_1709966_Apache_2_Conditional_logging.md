---
title: "Apache 2 Conditional logging"
date: 2011-03-19
forum: General Help
---

### Post by HugeLoad on 2011-03-19
Good Morning everyone!

I want to do some conditional logging in Apache 2

1. Remove any reference to robots.txt
2. Don't log pictures at all
3. Don't log 4 IP's which are admins (hundreds of log entries - just unnecessary)

After a massive amount of Googling over the past couple of days, I've come up with what I THINK are solutions to the above, but I have no idea how to combine them.

1. 

##Don't want any mention of robots.txt in logfiles
SetEnvIf Request_URI "^/robots\.txt$" dontlog
CustomLog /var/log/apache2/access.log combined env=!dontlog

2. 

## Don't want thousands of "pointless" image requests
SetEnvIf Request_URI \.gif image-request
SetEnvIf Request_URI \.jpg image-request
SetEnvIf Request_URI \.png image-request
CustomLog /path/to/log/access.log env=!image-request

3. 

## It seems as if I can't *eliminate* admin IP addy's so les's toss 'em in a "local" logfile
SetEnvIf  Remote_Addr   "192\.168\.1\."  local
SetEnvIf  Remote_Addr   "10\.1\.1\."         local
SetEnvIf  Remote_Addr   "1\.2\3\.44"         local
CustomLog               /path/to/log/local.log   common env=local
CustomLog               /path/to/log/access.log  common env=!local

Could some wise eyes take a look at the above - and - of equal importance, can I combine these directives within one conf file? OR should I "Include" these as modular external files (which seems a "cleaner" solution somehow) if so, how?

Regards & TIA for any suggestsions & guidance.

Hugey

---

