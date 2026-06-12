---
title: "Environmental Structure / Advice"
date: 2011-05-24
forum: General Help
---

### Post by ItsAsh on 2011-05-24
Hi Ubuntians!

I am seeking advice for an environmental structure I wish to implemented within my future server. I would be looking at installing Ubuntu 10.4 (server edition) on the dedicated server.

My goal is to understand how to accomplish the following task. I would like to have a site directory/structure whereby I can host the Development Environment, Staging Environment and the Production Environment.

1. The development environment would be the SVN Repository whereby (if a number of developers work on the same project, they each work on there own branch, and the changes are later merged into the main repository).

The development environment once complete is then cloned into the staging environment when approved is deployed into the production environment.

2. The structure I have in mind is the following, however please remember I may be required to use an SSL Certificate on some domain names.

This is the site root NOT accessible by end-user.
**/var/www/{DOMAIN.COM}/**

This is the development root, Accessible by end-user, only when a cookie or session is active.
**/var/www/{DOMAIN.COM}/development/**
**/var/www/{DOMAIN.COM}/development/trunk/**
**/var/www/{DOMAIN.COM}/development/tags/**
**/var/www/{DOMAIN.COM}/development/branches/**

This is the staging root, Accessible by end-user, only when a cookie or session is active.
**/var/www/{DOMAIN.COM}/staging/**

This is the production environment, the default site home directory.
**/var/www/{DOMAIN.COM}/production/**

My point is Developers work in development, customer reviews the changes in staging and production is the live environment. All changes are revised within SVN/development, and nothing is ever lost, or overwritten.

How could I make it so if you go to **[www.domain.com](www.domain.com)** it automatically goes to **/var/www/domain.com/production/index.php**.

If anyone would be able to assist me here, or perhaps give me advice where my plans are either ambiguous or could be improved?

Thank you in advance,
Ash!

---

