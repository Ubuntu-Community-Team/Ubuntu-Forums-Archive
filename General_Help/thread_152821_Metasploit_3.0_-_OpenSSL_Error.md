---
title: "Metasploit 3.0 - OpenSSL Error?"
date: 2006-03-30
forum: General Help
---

### Post by breuerp on 2006-03-30
When trying to run Metasploit Framework 3.0 I get the following error:

./lib/rex/proto/smb/crypt.rb:1:in `require': no such file to load -- openssl (LoadError)
        from ./lib/rex/proto/smb/crypt.rb:1
        from ./lib/rex/proto/smb.rb:4
        from ./lib/rex/proto.rb:2
        from ./lib/rex.rb:44
        from ./msfconsole:9

I know that I have Ruby 1.8 installed as well as OpenSSL.  Any ideas what I may be missing?

Cheers,
PCB

---

### Post by MindsX on 2006-04-07
sudo apt-get install libopenssl-ruby1.8

---

### Post by breuerp on 2006-04-25
No joy. Still working on it.  As near as I can tell OpenSSL is installed.  Heck, Synaptic tells me it's installed.

---

### Post by dougfir on 2006-06-29
I have the same problem with openssl.  I do:

taylor@zulu:/usr/src$ sudo apt-get install openssl
Reading package lists... Done
Building dependency tree... Done
openssl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
taylor@zulu:/usr/src$ ls -l
total 43368
lrwxrwxrwx  1 root src        28 2006-06-28 22:15 linux -> /usr/src/linux-source-2.6.15
drwxr-xr-x 19 root root     4096 2006-06-28 22:15 linux-headers-2.6.15-25
drwxr-xr-x  4 root root     4096 2006-06-28 22:12 linux-headers-2.6.15-25-386
drwxr-xr-x 20 root root     4096 2006-06-14 05:08 linux-source-2.6.15
-rw-r--r--  1 root root 44346806 2006-06-14 05:09 linux-source-2.6.15.tar.bz2
taylor@zulu:/usr/src$ pwd
/usr/src
taylor@zulu:/usr/src$



As you can see, I have no openssl in my /usr/src.

Where is it??

---

### Post by dom on 2006-07-13
> **dougfir said:**
> 

<snip>

As you can see, I have no openssl in my /usr/src.

Where is it??

in order to get the source, you need to do :

      apt-get source openssl

---

### Post by samad909 on 2007-08-27
try this

```

sudo aptitude install libopenssl-ruby

```

---

### Post by komputes on 2007-12-25
Installing Metasploit on Ubuntu/Kubuntu/Debian Linux

At this time, no package exists for Metasploit 3. In order to use the Metasploit Framework on Ubuntu or Debian distributions of Linux, the following packages need to be installed:

# apt-get install ruby libruby rdoc
# apt-get install libyaml-ruby
# apt-get install libzlib-ruby
# apt-get install libopenssl-ruby
# apt-get install libdl-ruby
# apt-get install libreadline-ruby
# apt-get install libiconv-ruby
# apt-get install rubygems *

*The RubyGems package may need to be manually downloaded and installed.

Once the dependencies have been installed, use the "gem" command to install version 1.2.2 of rails (required for the msfweb interface).

# gem install -v=1.2.2 rails

If you would like to use the experimental GUI, you will need to install the following packages:

# apt-get install libgtk2-ruby libglade2-ruby

If you would like to use the online update feature, you will need to install the "subversion" package as well. Once the pre-requisites have been installed, download the Unix tarball from Framework Website and extract it to the directory of your choice. If everything was installed correctly, execute the interface of your choice to get started (msfconsole, msfweb, etc).

---

