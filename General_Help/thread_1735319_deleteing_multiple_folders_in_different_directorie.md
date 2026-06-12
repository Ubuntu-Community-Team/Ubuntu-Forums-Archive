---
title: "deleteing multiple folders in different directories with filezilla."
date: 2011-04-21
forum: General Help
---

### Post by webcabbie on 2011-04-21
So I have a share hosting account with 60 sites all running wordpress. 

There is a plugin I want to delete from all 60 wordpress sites. 

The plugin is in the same path in all 60 sites. 

mysite.com/wp-content/plugins/carter
Is there a way I can search the entire home directory with filezilla or another ftp and delete every folder with that name in every site or I have to do it the tedious 1by1 sucky way?

---

### Post by spikoley on 2011-04-21
I don't think you can do that with an FTP program.  Do you have SSH access to the hosting server?

---

### Post by webcabbie on 2011-04-21
Im not sure.. all I know at this point is I have been using a plugin that was casuing my host to overload so they shut me down. 

I need to find a way to delete all these fast. Every second my sites are down I risk my SERPs dropping.

There is a search I am trying to play with the options to see if I can get them to pop up.

---

### Post by webcabbie on 2011-04-21
Filezilla has a search option. 

Search directory /

That would be the entire home directory right?

Than you can select from dropdowns

Path   Ends With if I input /wp-content/plugins/carter

It should only find me and allow me to delete those files right? 

I am running it now but it's searching like crazy and I think showing me all those files and everything they contain.

---

### Post by deathadder on 2011-04-21
If you've got a linux machine you could add the servers name, login and password to your ~/.netrc and then write a bash script to ftp to your shared host and delete the required files. 

Something like:
```
vi ~/.netrc
machine yoursharedhost.com
login yourFtpUsername
password yourFtpPassword

```
Then you'll need to chmod 600 that file:
```

chmod 600 ~/.netrc

```
Then write a bash script, something along these lines should help.
```

myHosts=(site1 site2 anotherSite)

for site in "$myHosts[@]" do
   ftp yoursharedhost.com << END_SCRIPT
   cd $site
   cd wp-content/plugins
   rmdir carter/
   quit
   END_SCRIPT
done

```
Unfortinuately that'll make a ftp connection for each host, I'm not sure if you can write it so that bash will cd into $site/wp-content/plugins and remove the carter directory for each site as part of the FTP command...

I don't know of any other way to do it I'm afraid.

---

