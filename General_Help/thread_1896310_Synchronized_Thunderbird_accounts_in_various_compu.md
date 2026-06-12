---
title: "Synchronized Thunderbird accounts in various computers"
date: 2011-12-16
forum: General Help
---

### Post by BC59 on 2011-12-16
I spent a lot of time trying to find a solution for my email synchronization. I use since years Thunderbird as email client.

The problem is that I use at least 2 computers and I need my emails in both. So far I'm using Gmail but is not the same. Especially if you take into account that Gmail is refreshing the mail every 40-60 minutes. I need my messages instantaneously and I need a decent email application.

So if I use Thunderbird in my 2 computers, I have separate and different Inbox and Sent folders. Not speaking about Address book.

The solution could be the installation of [Portable Thunderbird]("http://http://portableapps.com/apps/internet/thunderbird_portable") on a USB, but I don't like to have all my messages in an external drive, which is very easy to loose.

So I found that a possible solution could be the installation of the account folder on Dropbox (or Ubuntu One).

To do this you need a [Dropbox]("http://http://www.dropbox.com/") account. Then **copy** the /.thunderbird hidden folder from /home to Dropbox folder.
In Linux /.thunderbird folder, the application is storing the mails and the address book.

Now you have to open the /.thunderbird folder in /home and edit the file **profiles.ini**.
Open it with Gedit and change the path towards the new place.
It is like this:
> [General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=[COLOR="blue"]1[/COLOR]
Path=[COLOR="Blue"]your_account_Number[/COLOR]

Change it to like this:
> [General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=[COLOR="blue"]0[/COLOR]
Path=/home/[COLOR="blue"]your_name[/COLOR]/Dropbox/.thunderbird/[COLOR="blue"]your_account_Number[/COLOR].default


Pay a lot of attention to change the value of IsRelative from 1 to 0

Open Thunderbird to check if recognises the new account place. Go to Edit--Preferences--Server Settings--Local Directory to see if in the box is shown the new path.

Now you have to do exactly the same to the other computer. Install Dropbox, sychronize and change the **profiles.ini** like before, to change the path.

It's done. Both computers should have fully synchronized Thunderbird.

_Problems_

The solution is not perfect, because Dropbox is creating conflicted copies of the mail files. To the moment, not a big deal, but I'm trying to find why is doing that.
I think it's better to rename the computers to have the same account name, because Thunderbird is a little confused.
Furthermore has to be installed the same version of Thunderbird in both computers.

If you try it, please post your opinion and possible workarounds to make it work better.

---

