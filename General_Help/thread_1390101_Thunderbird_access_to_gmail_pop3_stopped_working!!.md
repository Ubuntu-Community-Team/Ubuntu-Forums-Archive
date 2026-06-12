---
title: "Thunderbird access to gmail pop3 stopped working?!?!"
date: 2010-01-25
forum: General Help
---

### Post by chaeron on 2010-01-25
I had Thunderbird 2.0 (most resent 2.0 version) working fine with gmail pop3 access.

Then recently it just stopped working.  No requests for passwords....no errors popped up or logged...nothing.

When I click on get mail for a gmail pop3 account (pop.gmail.com, port 995, ssl), TBird does nothing. The status bar shows nothing.....like it's silently not even trying to look up the gmail pop server, nor trying to contact it.

If I change to not use ssl (eg. port 110) it will try to access the gmail server, but fails (of course) since gmail requires ssl and port 995.

If I'm going through a mail proxy (PopFile spam filter), then everything works fine, but then the local hop is not SSL and on port 110, and the proxy is the one that uses ssl/995, which probably explains why that works.  But when I'm on the road, I can't use my proxy and need direct access to gmail on my laptop.

Some notes:

1) Access to non-ssl pop3 (eg. port 110) mail servers works fine with TBird.
2) Evolution seems to be able to access my gmail pop accounts just fine (so I know that pop is configured on gmail just fine), and so it's not a firewall/port issue.
3) Deleting and reconfiguring accounts doesn't help.
4) Reinstalling tbird doesn't help.

I suspect some weird config corruption with TBird, something specifically to do with ssl access.

Anyone have any ideas what might be causing this?  TBird is my standard email tool on all machines and I'ld really like to get it working again on my Ubuntu (Karmic) laptop.

Thanks!

---

### Post by chaeron on 2010-01-28
I resolved this today.

Uninstalled TBird 2.0.  Installed Thunderbird 3.0 using the ubuntuzilla repository.  Did the copy .mozilla-thunderbird to .thunderbird trick to migrate all my mailboxes and such so that 3.0 could find it, and that has resolved the issue.  I'm now accessing gmail fine again.

Who knows what the problem with 2.0 was, since it worked for a long time.

Onwards and upwards! ;-)

Though not having the latest stable 3.0.1 build of TBird in the ubuntu repositories was a kick in the nads.  What are the repository maintainers thinking?

Oh?!?!

I guess they're not.

---

