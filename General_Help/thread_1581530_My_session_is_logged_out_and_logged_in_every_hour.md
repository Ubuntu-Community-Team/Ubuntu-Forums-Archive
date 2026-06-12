---
title: "My session is logged out and logged in every hour"
date: 2010-09-25
forum: General Help
---

### Post by ninozor on 2010-09-25
Hello. I explain my problem.

I need to know why my computer is logged out and logged in every hour.

The crontab hasn't task:

[I]noenan@pepinaco:~$ crontab -l
no crontab for noenan
noenan@pepinaco:~$ sudo crontab -u root -l 
no crontab for root
[/I]

What Can I do or test? 
 

The SO is Ubuntu 10.04

I attach my system log:



Log: 
[I]Sep 19 08:17:01 pepinaco CRON[8479]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 08:17:01 pepinaco CRON[8479]: pam_unix(cron:session): session closed for user root
Sep 19 09:17:01 pepinaco CRON[8945]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 09:17:01 pepinaco CRON[8945]: pam_unix(cron:session): session closed for user root
Sep 19 10:17:01 pepinaco CRON[9499]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 10:17:01 pepinaco CRON[9499]: pam_unix(cron:session): session closed for user root
Sep 19 11:17:01 pepinaco CRON[10091]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 11:17:01 pepinaco CRON[10091]: pam_unix(cron:session): session closed for user root
Sep 19 12:17:01 pepinaco CRON[10919]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 12:17:01 pepinaco CRON[10919]: pam_unix(cron:session): session closed for user root
Sep 19 13:17:01 pepinaco CRON[11408]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 13:17:01 pepinaco CRON[11408]: pam_unix(cron:session): session closed for user root
Sep 19 14:17:01 pepinaco CRON[11914]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 14:17:01 pepinaco CRON[11914]: pam_unix(cron:session): session closed for user root
Sep 19 15:17:01 pepinaco CRON[12776]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 15:17:01 pepinaco CRON[12776]: pam_unix(cron:session): session closed for user root
Sep 19 15:51:06 pepinaco polkitd(authority=local): Unregistered Authentication Agent for session /org/freedesktop/ConsoleKit/Session18 (system bus name :1.564, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale es_ES.UTF-8) (disconnected from bus)
Sep 19 15:51:06 pepinaco kdm: :0[26390]: pam_unix(kdm-np:session): session closed for user noenan
Sep 19 15:51:06 pepinaco gnome-keyring-daemon[26460]: dbus failure unregistering from session: Connection is closed
Sep 19 15:51:07 pepinaco gnome-keyring-daemon[26460]: dbus failure unregistering from session: Connection is closed
Sep 19 15:51:10 pepinaco kdm: :0[13183]: pam_unix(kdm-np:session): session opened for user noenan by (uid=0)
Sep 19 15:51:10 pepinaco kdm: :0[13183]: pam_ck_connector(kdm-np:session): nox11 mode, ignoring PAM_TTY :0
Sep 19 15:51:15 pepinaco polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session19 (system bus name :1.604 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale es_ES.UTF-8)
Sep 19 15:51:51 pepinaco gnome-keyring-daemon[13256]: PROMPT INPUT:#012#012[prompt]#012title=Desbloquear el depósito de inicio#012primary=Introducir la contraseña para desbloquear el depósito#012secondary=El depósito de inicio de sesión no se desbloqueó cuando inició sesión en su equipo.#012window-id=#012#012[visibility]#012name_area=false#012confirm_area=false#012password_area=true#012#012[transport]#012public=0320E218925F6960405A1B683D7C4D09F64C46CAFD89BCBA98E48CE382084B0ACE9D4BC942ED0267F77194ED5F2C008167BFB5166C270F06DA4983C463DBC1332087447E7CEF81A3C9168CBF24FC2A10120D65705B72A7AB4482ED56DD58DEFE6EA2E66D48990206093B2164F9D75B2CC0E8243568329481E673F6B87BF486F30627C5EC9701AF81514952DB0CF595E7DD36C7DC3E3155F799170FE6F36CBCC5BD4ED231DE3130AF1C552BABD754AB5C7F6C82E6F3C5F15D120B673B0BA57CA3#012prime=FFFFFFFFFFFFFFFFC90FDAA22168C234C4C6628B80DC1CD129024E088A67CC74020BBEA63B139B22514A08798E3404DDEF9519B3CD3A431B302B0A6DF25F14374FE1356D6D51C245E485B576625E7EC6F44C42E9A637ED6B0BFF5CB6F406B7EDEE386BFB5A899FA5AE9F24117C4B1FE649286651ECE45B3DC2007CB8A163BF0598DA48361C55D39A69163FA8FD24CF5F83655D23DCA3AD961C62F356208552BB9ED529077096966D670C354E4ABC9804F1746C08CA237327FFFFFFFFFFFFFFFF#012base=02#012
Sep 19 15:52:01 pepinaco gnome-keyring-daemon[13256]: PROMPT OUTPUT:#012#012[transport]#012public=7F9C5C416D6B4E26A91CB3268195C22ED31AFCF8E175E5D2B4D290CABCE1BC637B9A2BE8F5A856E163645643AE77F201C4325C32103924CAB60AFDCF58A293D505D9D1A3ADC05A932BCF8FCDA50CFCDA541D375935C78A2839E471B0A2AE21800D27857934AF27BD6D1E45DE7F97EB7279E0FE6DADD6A87D987303FCE83E2BE925EA5931044514340298B53F2D18444A677DA417B89A99803091091A21EC187D3A06345BFFC5AAFC88710D7F02AD86E880B7084AC307C462C1EB490C30274D37#012#012[password]#012parameter=CB81A0BABED88EDB28DE9FBA76C375F3#012value=3E4FBB2DDF6C1F9137BA2B03D0967BA9#012#012[unlock-options]#012unlock-auto=false#012unlock-timeout=0#012unlock-idle=0#012#012[details]#012expanded=false#012#012[prompt]#012response=ok#012
Sep 19 16:17:01 pepinaco CRON[16223]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 16:17:01 pepinaco CRON[16223]: pam_unix(cron:session): session closed for user root
Sep 19 17:17:01 pepinaco CRON[23301]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 17:17:01 pepinaco CRON[23301]: pam_unix(cron:session): session closed for user root
Sep 19 18:17:01 pepinaco CRON[26330]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 18:17:01 pepinaco CRON[26330]: pam_unix(cron:session): session closed for user root
Sep 19 19:17:01 pepinaco CRON[27659]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 19:17:01 pepinaco CRON[27659]: pam_unix(cron:session): session closed for user root
Sep 19 20:17:01 pepinaco CRON[28839]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 20:17:01 pepinaco CRON[28839]: pam_unix(cron:session): session closed for user root
Sep 19 21:17:01 pepinaco CRON[30014]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 21:17:01 pepinaco CRON[30014]: pam_unix(cron:session): session closed for user root
Sep 19 22:17:01 pepinaco CRON[31848]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 22:17:01 pepinaco CRON[31848]: pam_unix(cron:session): session closed for user root
Sep 19 23:17:01 pepinaco CRON[32222]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 23:17:01 pepinaco CRON[32222]: pam_unix(cron:session): session closed for user root
Sep 20 00:17:01 pepinaco CRON[825]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 00:17:01 pepinaco CRON[825]: pam_unix(cron:session): session closed for user root[/I]

---

### Post by robsoles on 2010-09-25
welcome to UF.

Anyone is going to need more info to start tackling your puzzle.


What version of which distro are you running there? (Ubuntu 10.04 64 bit latest is mine for instance)

Was that installed as desktop or server? (Do you get GUI/Desktop or is it all text based?)

Are you logged in as root on purpose?

Are you logged into this session locally or remotely?


I'm betting on lots of questions both ways to solve this one!

---

### Post by robsoles on 2010-09-26
> **robsoles said:**
> welcome to UF.

Anyone is going to need more info to start tackling your puzzle.


What version of which distro are you running there? (Ubuntu 10.04 64 bit latest is mine for instance)

Was that installed as desktop or server? (Do you get GUI/Desktop or is it all text based?)

Are you logged in as root on purpose?

Are you logged into this session locally or remotely?


I'm betting on lots of questions both ways to solve this one!


That was silly of me, looked closer at your log entries and they are just the log entries generated by the crontab hourly task - I was wrong, no questions either way are really required.

[www.google.com/search?q=crontab+hourly+tasks](www.google.com/search?q=crontab+hourly+tasks) may or may not shed more light on what is happening for you.

---

