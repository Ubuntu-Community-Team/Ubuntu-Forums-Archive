---
title: "Weird Postfix/Dovecot Problem"
date: 2012-03-09
forum: General Help
---

### Post by NapoleoneXIV on 2012-03-09
EDIT:  I think I just fixed it, so this may be moot.  Sorry for the trouble!  I'd delete the thread, but it doesn't seem to be an option.

I have been running a small email server for my family for about 5 years now (still running 8.04) and it has been working pretty well and without issue.  Today, however, it decided to suddenly stop working for reasons I can't for the life of me figure out (I haven't changed *any* settings in ages).  And now after about 7 hours of trying to fix it myself, I'm basically at my wits end.

Here's what is happening:

The server essentially can't receive any email from any source.  I've been trying to have local email addresses email themselves via Thunderbird with no luck.  Likewise, I can't receive email from external sites like Yahoo.  Notably, when emailing to my server, the email doesn't get bounced.  It kind of just disappears into the ether.  The only email that I can receive is via command line.  That is, "mailx [email]local@mydomain.com[/email]" works fine, but that's it.

Meanwhile, the server can email out to anyplace (but itself) fine.  However, the "mailx" command doesn't work to email external sites.  

The log files disclose literally no errors (both the mail log in /var/log/ and the dovecot delivery log) at this point.

What I tried to do was a complete uninstall and reinstall of both Postfix and Dovecot following, roughly, this guide:
[http://library.linode.com/email/postfix/dovecot-mysql-ubuntu-10.04-lucid](http://library.linode.com/email/postfix/dovecot-mysql-ubuntu-10.04-lucid)
But I haven't had any real luck with that.

Has anyone ever dealt with a similar situation, or have some idea of what's the matter?  For my part, I'm completely out of ideas at this point.


Here is my Postfix main.cf file, if it's any help in diagnosing the problem:
> # See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = /usr/share/doc/postfix

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

data_directory = /var/lib/postfix

myhostname = out-post.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.out-post.net, localhost, localhost.out-post.net
relayhost = mail.optonline.net
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
html_directory = /usr/share/doc/postfix/html
message_size_limit = 30720000
virtual_alias_domains = 
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
virtual_create_maildirsize = yes
virtual_maildir_extended = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
virtual_transport = dovecot
dovecot_destination_recipient_limit = 1

Please let me know if there's anything else I can post that will be of any help in figuring out the problem.  Also, sorry if I posted this in the wrong place.  Sorry if I did, and please do move it to the right place if it's not too much trouble.

---

