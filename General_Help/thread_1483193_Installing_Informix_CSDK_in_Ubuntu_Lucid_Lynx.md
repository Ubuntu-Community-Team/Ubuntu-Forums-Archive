---
title: "Installing Informix CSDK in Ubuntu Lucid Lynx"
date: 2010-05-14
forum: General Help
---

### Post by jbatista on 2010-05-14
Dear all,

I've tried to install the IBM Informix Client Software Development Kit (CSDK) in Ubuntu Lucid Lynx (10.04) this week. Since this is not a package bundled with Ubuntu, a bug report on its own would not make sense. But I'm posting my experience here so that others attempting to install it on their Linuxes might also benefit from it, hopefully to give hints on some possible installation frustrations.

Since the standard Lucid installation appears to prefer the Java OpenJDK instead of the Sun JDK, it does not include the more common Sun Java (will, actually now it's really from Oracle since it bought Sun). However, the Informix installer is a Java Archive (jar) package which I found out *really* needs the Sun Java instead of the OpenJDK! 
(Can't really blame IBM ... it's a company, its business is making money from their products, so they make the decisions and we have no say on it except to accept or reject it.)

During installation, 
```
./installclientsdk
```I kept coming up with the following error:
```
The wizard cannot continue because of the following error: could not load wizard specified in /wizard.inf (104)
```Running the installer with 
```
java -Dis.debug=1 -jar csdk.jar
```I found that one class appears to be missing:
```
com.jxml.quick.QPE: java.lang.ClassNotFoundException: sun.beans.editors.BoolEditor
```because the InstallShield installer expects that the only Java Runtime Engine out there is from Sun and everyone is running it... So it's not really Oracle's fault, or Sun's fault ... rather it's InstallShield's, which then again it makes it Sun's, because they chose Java to install something that turns out to be installable from the console! :confused:

Did I mention I hate Java? No? Well, let me tell you right now: I **HATE** Java :mad:
This dependence hell really tests one's patience... But I digress.

Anyway, I'm posting this here and hopefully the popular search engines will provide hints that might help others who might find themselves in a similar predicament.

1. You also need to create a "*informix*" user. If you've already tried running the installer, I'm sure you already got a message about this. Simply create a "informix" user, make its home to be in /opt/informix (for example) and try again. Create an "informix" user with user ID below 1000 (so it does not show in the login screen), for example 201. Also create an "informix" group (with group ID 201, for example) and make user informix belong to this group. The home can be /opt/informix if you choose to install the CSDK there. You can turn off the login ability (i.e. make the default shell to be e.g. /bin/false ).

2. Next, you'll need to install Sun Java (oh boy...). 
According to instructions here: [http://www.ubuntu.com/getubuntu/releasenotes/1004#Sun%20Java%20moved%20to%20the%20Partner%20repository](http://www.ubuntu.com/getubuntu/releasenotes/1004#Sun%20Java%20moved%20to%20the%20Partner%20repository)
you have to do (as root, of course):
```

add-apt-repository "deb http://archive.canonical.com/ lucid partner"
apt-get update
apt-get install sun-java6-jre

```
Note: I installed more than the sun-java6-jre because I have quite some room to spare and I didn't want to bother trying to see the minimum requirements for this to work. I did not test if more packages were needed, so run an "apt-get cache java6" and find which packages are vailable from the Lucid "partner" repository.

3. Now the magic step:
```
./installclientsdk -javahome /usr/lib/jvm/java-6-sun/jre/
```Only this JRE will make it work... :mad: :mad: :mad:

From then on it should be breeze. Next, next, next...
If you want, you can remove the sun-java6-* packages after installation, since we only need those for this step... (unless you expect to do Java stuff with Informix again, then I suspect you might want to keep the sun-java6 packages).

Also, remember to **read the terms of use carefully** before accepting the installation, because this is not free software, it is licensed by IBM and so Canonical has nothing to do with it. Unfortunately, I'm on a personal project to develop C++ software that uses the Informix client, so I had to go through with all this.

Hope this helps.

---

### Post by Kyntero on 2010-06-10
Muchas,Muchas,Muchas,Muchas,Muchas,Muchas,Muchas,Muchas,Muchas,Muchas,Muchas,Muchas,Muchas,Muchas **gracias**

thank you very, much, much, much, much, much, much, much, much, much, much, much, much

**Muito obrigado**

Saludos desde Colombia
Greetings from Colombia
[COLOR=#000000]saudações de[/COLOR] Colombia

---

### Post by cpudney on 2010-08-10
G'day,

I recently stumbled across this error message too when running an *InstallShield* installer.

The solution as you point out is to make sure you [use Sun's JRE rather than the default OpenJDK JRE]("http://ubuntu-linux-dell-inspiron-9400.blogspot.com/2010/08/installshield-wizard-fails-with-openjdk.html").

I added a couple of steps after installing the sun-java6-* packages:

[LIST=1]
[*]Update your java alternatives to use Sun's JRE.  Then you don't need to manually specify the path to the JRE on the command-line; the installer will pick it up automatically.```
sudo update-java-alternatives -v -s java-6-sun
```
[*]Remove all OpenJDK packages.  You don't need both and Sun's JRE is superior IMHO.
[/LIST]

---

### Post by raulpinpla on 2011-06-12
Hello i'm having a problem with the installation of Informix CSDK... well i think is that..  my problen is taht i need a LAMP server width informix and mssql support, then i already install CSDK witout problem and mysql and apache2 but when i try to compile the php5.2.0 i get this error:

*** Warning: Linking the shared library libphp5.la against the non-libtool
*** objects  /opt/informix/lib/esql/checkapi.o is not portable!
/usr/bin/ld: cannot find ext/informix/: File format not recognized
collect2: ld returned 1 exit status
make: *** [libphp5.la] Error 1

i'm not a experimented user in ubuntu server and i dont know what to do to fix it.

please i really appreciate if you can help me.

---

