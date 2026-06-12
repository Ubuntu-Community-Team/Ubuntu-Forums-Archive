---
title: "Plesk 9.3.0 + ubuntu 8.04"
date: 2010-03-20
forum: General Help
---

### Post by FewG on 2010-03-20
Hello, I have a problem, until today Plesk 9.3.0 works finely on my ubuntu 8.04 dedicated server. Then i tried to install proFTPd and after that Plesk chashs.
Now i want to reinstall my plest but i have a problem i get lots of error messanges like that > 
E: Sub-process /usr/bin/dpkg returned an error code (1)
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy Release.gpg
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates Release.gpg
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-proposed Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy Release
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-proposed Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/main Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/restricted Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/restricted Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/main Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/universe Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/universe Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-proposed/restricted Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-proposed/main Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-proposed/multiverse Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-proposed/universe Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-proposed/restricted Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-proposed/main Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-proposed/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-proposed/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Reading package lists...
ERROR: An error occurred on attempt to install packages.
Achtung! Ihre Software ist vielleicht nicht betriebsbereit.
Bitte kontaktieren Sie den technischen Produktsupport.
root@lineage:~#    How can I remove completly plesk and install it again?

---

### Post by FewG on 2010-03-20
install_log  (web-interface)

```

Getting packages to installation list:
 skip package 'plesk-base-9.3.0-ubuntu8.04.build93091230.07.amd64' from   component base - there is same or newer version of this package is   installed (in system  plesk-base-9.3.0-ubuntu8.04.build93091230.07.amd64)
 skip package 'psa-locale-base-en-us-9.3.0-2009121611.all' from   component base - there is same or newer version of this package is   installed (in system psa-locale-base-en-us-9.3.0-2009121611.all)
 skip package 'psa-mod-fcgid-configurator-1.0.1-0.97049.amd64' from   component base - there is same or newer version of this package is   installed (in system psa-mod-fcgid-configurator-1.0.1-0.97049.amd64)
 skip package 'psa-pylibplesk-9.3.0-ubuntu8.04.build93091230.07.all'   from component base - there is same or newer version of this package is   installed (in system   psa-pylibplesk-9.3.0-ubuntu8.04.build93091230.07.all)
 skip package 'log4cpp-plesk-0.3.5rc2-v9.275143.amd64' from component   pmm-ded - there is same or newer version of this package is installed   (in system log4cpp-plesk-0.3.5rc2-v9.275143.amd64)
 skip keypackage 'samba-3.0.28a-1ubuntu4.10.amd64' from component   psa-fileserver - there is same or newer version of this package is   installed (in system samba-3.0.28a-1ubuntu4.10.amd64)
autoinstaller: read output of apt-cache policy mailman 2>/dev/null   with popen
Installation started in background
autoinstaller: pclose OK
Package mailman with version '1:2.1.9-9ubuntu1' is available from apt
Following packages will be installed:   libpam-plesk-9.3.0-ubuntu8.04.build93091230.07.amd64   plesk-skins-9.3.0-0.287499.all   psa-9.3.0-ubuntu8.04.build93091230.07.amd64   psa-api-9.3.0-ubuntu8.04.build93091230.07.amd64   psa-awstats-configurator-1.0.0-ubuntu8.04.build93091230.07.all   psa-proftpd-1.3.1-ubuntu8.04.build93091230.07.amd64   psa-proftpd-inetd-1.3.1-ubuntu8.04.build93091230.07.amd64   psa-updates-9.3.0-ubuntu8.04.build93091230.07.all   psa-autoinstaller-3.5.0-090817.16.amd64   psa-php5-configurator-1.5.1-ubuntu8.04.build93091230.07.all   psa-appvault-advancedpoll-2.03-8203720080327022632.all   psa-appvault-anyinventory-2.0-8202820080327022636.all   psa-appvault-articlepublisher-1.0-8200920080327022644.all   psa-appvault-autoindex-2.2.4-8200220080327022653.all   psa-appvault-avactis-1.8.1-8200720080327022715.all   psa-appvault-b2evolution-0.9.0.12-8203020080327022753.all   psa-appvault-bbclone-0.49-8200520080820033040.all   psa-appvault-brim-2.0.0-8203120080327022831.all   psa-appvault-coppermine-1.4.16-8200220080327022857.all   psa-appvault-cs-cart-1.3.5-8201220080327022957.all   psa-appvault-cslh-2.14.5-8200220080327023118.all   psa-appvault-cubecart-4.2.0-8200220080327023133.all   psa-appvault-docfaq-1.71-8203720080327023148.all   psa-appvault-dolphin-6.0.0-8201020080327023206.all   psa-appvault-drupal-6.1-8200320080327023245.all   psa-appvault-easybiller-1.0-8200120080404001639.all   psa-appvault-easysnaps-2.0-8200120080404001700.all   psa-appvault-egroupware-1.4.002-8201220080327023358.all   psa-appvault-emuwebmail-7.0.1-8200720080327023522.all   psa-appvault-eswap-1.0-8200220080404001727.all   psa-appvault-gallery-2.2-8201720080327023726.all   psa-appvault-geeklog-1.4.1-8200320080327024040.all   psa-appvault-gtchat-0.93-8003020080327024110.all   psa-appvault-helpcenterlive-2.1.5-8200220080327024115.all   psa-appvault-joomla-1.5.1-8200720080405023108.all   psa-appvault-knowledgetreeoss-3.4.5-8200820080327024234.all   psa-appvault-mailer-6.3-8200420080609232516.all   psa-appvault-mambo-4.6.2-8201520080327024329.all   psa-appvault-mantis-1.1.1-8200320080426054935.all   psa-appvault-mediawiki-1.11.0-8200920080327024423.all   psa-appvault-merchant-5.3-8003020080416013305.all   psa-appvault-moodle-1.8-8202920080327024531.all   psa-appvault-movabletype-4.0-8201520080415002955.all   psa-appvault-multicart-2.0-8200120080404001742.all   psa-appvault-myorgbook-2.8-8202720080327024652.all   psa-appvault-noahclass-1.3-8205520080327024657.all   psa-appvault-nucleus-3.21-8203220080327024701.all   psa-appvault-onebiz-8.0-8200120080405021240.all   psa-appvault-openbiblio-0.5-8204720080327024706.all   psa-appvault-oscommerce-2.2ms2-8206120080327024714.all   psa-appvault-osticket-1.3.0-8203320080327024721.all   psa-appvault-owl-0.80-8203620080327024726.all   psa-appvault-phpads-2.0.8-8203520080327024738.all   psa-appvault-phpbook-1.50-8203220080327024809.all   psa-appvault-phpbugtracker-1.19-8203820080416050605.all   psa-appvault-phpdig-1.85-8203120080327024817.all   psa-appvault-phpmoney-1.3-8204320080327024822.all   psa-appvault-phpmyfamily-1.4.1-8203420080327024828.all   psa-appvault-phpmyvisites-2.3-8202820080327024834.all   psa-appvault-phprojekt-5.2-8200820080327024849.all   psa-appvault-phpsurveyor-0.98-8204320080327024905.all   psa-appvault-phpwebsite-0.10.2-8203420080327024918.all   psa-appvault-phpwiki-1.3.11-8204320080327024942.all   psa-appvault-pinnacle-cart-3.5.2-82059720080408070143.all   psa-appvault-plog-1.0-8203620080327025002.all   psa-appvault-pmachinefree-2.4-8203520080327025015.all   psa-appvault-postnuke-0.761a-8205620080327025030.all   psa-appvault-ray-3.0.0-8201220080412085531.all   psa-appvault-serendipity-1.1.2-8203020080327035434.all   psa-appvault-siteframe-3.2.2-8202920080327035503.all   psa-appvault-smf-1.1.2-8203320080327035512.all   psa-appvault-socialware-1.0-8200120080404001947.all   psa-appvault-ssm-1.0-8203720080327035522.all   psa-appvault-sugarcrm-5.0.0-8201220080327035551.all   psa-appvault-supportcenter-2.5.2-8200820080327035928.all   psa-appvault-supportdesk-3.0-8200120080404002110.all   psa-appvault-tellme-1.2-8202720080327035955.all   psa-appvault-tikiwiki-1.9.7-8203920080327040016.all   psa-appvault-tutos-1.88-8203820080327040120.all   psa-appvault-typo3-4.0-8202020080424050531.all   psa-appvault-uebimiau-2.7.8-8203720080327040218.all   psa-appvault-updates-9.3.0-ubuntu8.04.build93091230.07.all   psa-appvault-vivvocms-4.0.0-8200720080327040225.all   psa-appvault-webcalendar-1.0.5-8201020080327040236.all   psa-appvault-webshopmanager-2.0-8203120080327040241.all   psa-appvault-wordpress-2.3.3-8200520080412062207.all   psa-appvault-xoops-2.2-8204820080327040255.all   psa-appvault-xrms-1.19-8203120080415030843.all   psa-appvault-xtcommerce-3.0.4-8200920080327040328.all   psa-api-rpc-9.3.0-ubuntu8.04.build93091230.07.amd64   psa-migration-agents-9.3.0-ubuntu8.04.build93091230.07.amd64   psa-migration-manager-9.3.0-ubuntu8.04.build93091230.07.amd64   sb-publish-3.0.1-0.97008.all plesk-billing-6.0.4-20090625.11.all   psa-tomcat-configurator-9.3.0-ubuntu8.04.build93091230.07.amd64   psa-rubyrails-configurator-1.1.6-ubuntu8.04.build93091230.07.amd64   psa-firewall-1.0.1-ubuntu8.04.build93091230.07.amd64   psa-vpn-1.0.1-ubuntu8.04.build93091230.07.amd64   psa-fileserver-1.0.0-ubuntu8.04.build93091230.07.amd64   sshterm-0.2.2-9.278624.all   psa-watchdog-2.0.3-ubuntu8.04.build93091230.07.amd64   psa-cs-gs-2.0.0-ubuntu8.04.build93091230.07.amd64   psa-bf1942-1.0.0-ubuntu8.04.build93091230.07.amd64   psa-bf2-1.0.0-ubuntu8.04.build93091230.07.amd64   psa-mailman-configurator-9.3.0-ubuntu8.04.build93091230.07.all   mailman-1:2.1.9-9ubuntu1   psa-spamassassin-9.3.0-ubuntu8.04.build93091230.07.amd64   psa-backup-manager-9.3.0-ubuntu8.04.build93091230.07.amd64   psa-ftputil-1:2.1.1-0.98221.all psa-atis-1.0-50.amd64   psa-locale-de-de-9.3.0-2009121410.all   psa-locale-ja-jp-9.3.0-2009121410.all   psa-locale-es-es-9.3.0-2009121410.all   psa-locale-ru-ru-9.3.0-2009121410.all   psa-locale-fr-fr-9.3.0-2009121410.all   psa-locale-it-it-9.3.0-2009121410.all   psa-locale-zh-cn-9.3.0-2009121410.all   psa-locale-zh-tw-9.3.0-2009121410.all   psa-locale-nl-nl-9.3.0-2009121410.all   psa-horde-3.1.7-ubuntu8.04.build93091230.07.amd64   psa-imp-4.1.6-ubuntu8.04.build93091230.07.amd64   psa-ingo-1.1.5-ubuntu8.04.build93091230.07.amd64   psa-kronolith-2.1.8-ubuntu8.04.build93091230.07.amd64   psa-mimp-1.0.2-ubuntu8.04.build93091230.07.amd64   psa-mnemo-2.1.2-ubuntu8.04.build93091230.07.amd64   psa-passwd-3.0.1-ubuntu8.04.build93091230.07.amd64   psa-turba-2.1.7-ubuntu8.04.build93091230.07.amd64   psa-atmail-1:1.02-ubuntu8.04.build93091230.07.amd64 
 ----------------
Checking whether the package dependencies are resolved.
autoinstaller: read output of DEBIAN_FRONTEND=noninteractive LANG=C   apt-get --assume-yes --show-upgraded --purge --list-cleanup   --no-reinstall -o Dpkg::options::=--force-confdef -o   Dpkg::options::=--force-confold -o APT::Get::AllowUnauthenticated=true   -t 'hardy*' --just-print install   libpam-plesk=9.3.0-ubuntu8.04.build93091230.07   plesk-skins=9.3.0-0.287499 psa=9.3.0-ubuntu8.04.build93091230.07   psa-api=9.3.0-ubuntu8.04.build93091230.07   psa-awstats-configurator=1.0.0-ubuntu8.04.build93091230.07   psa-proftpd=1.3.1-ubuntu8.04.build93091230.07   psa-proftpd-inetd=1.3.1-ubuntu8.04.build93091230.07   psa-updates=9.3.0-ubuntu8.04.build93091230.07   psa-autoinstaller=3.5.0-090817.16 psa-php5-configurator   psa-appvault-advancedpoll=2.03-8203720080327022632   psa-appvault-anyinventory=2.0-8202820080327022636   psa-appvault-articlepublisher=1.0-8200920080327022644   psa-appvault-autoindex=2.2.4-8200220080327022653   psa-appvault-avactis=1.8.1-8200720080327022715   psa-appvault-b2evolution=0.9.0.12-8203020080327022753   psa-appvault-bbclone=0.49-8200520080820033040   psa-appvault-brim=2.0.0-8203120080327022831   psa-appvault-coppermine=1.4.16-8200220080327022857   psa-appvault-cs-cart=1.3.5-8201220080327022957   psa-appvault-cslh=2.14.5-8200220080327023118   psa-appvault-cubecart=4.2.0-8200220080327023133   psa-appvault-docfaq=1.71-8203720080327023148   psa-appvault-dolphin=6.0.0-8201020080327023206   psa-appvault-drupal=6.1-8200320080327023245   psa-appvault-easybiller=1.0-8200120080404001639   psa-appvault-easysnaps=2.0-8200120080404001700   psa-appvault-egroupware=1.4.002-8201220080327023358   psa-appvault-emuwebmail=7.0.1-8200720080327023522   psa-appvault-eswap=1.0-8200220080404001727   psa-appvault-gallery=2.2-8201720080327023726   psa-appvault-geeklog=1.4.1-8200320080327024040   psa-appvault-gtchat=0.93-8003020080327024110   psa-appvault-helpcenterlive=2.1.5-8200220080327024115   psa-appvault-joomla=1.5.1-8200720080405023108   psa-appvault-knowledgetreeoss=3.4.5-8200820080327024234   psa-appvault-mailer=6.3-8200420080609232516   psa-appvault-mambo=4.6.2-8201520080327024329   psa-appvault-mantis=1.1.1-8200320080426054935   psa-appvault-mediawiki=1.11.0-8200920080327024423   psa-appvault-merchant=5.3-8003020080416013305   psa-appvault-moodle=1.8-8202920080327024531   psa-appvault-movabletype=4.0-8201520080415002955   psa-appvault-multicart=2.0-8200120080404001742   psa-appvault-myorgbook=2.8-8202720080327024652   psa-appvault-noahclass=1.3-8205520080327024657   psa-appvault-nucleus=3.21-8203220080327024701   psa-appvault-onebiz=8.0-8200120080405021240   psa-appvault-openbiblio=0.5-8204720080327024706   psa-appvault-oscommerce=2.2ms2-8206120080327024714   psa-appvault-osticket=1.3.0-8203320080327024721   psa-appvault-owl=0.80-8203620080327024726   psa-appvault-phpads=2.0.8-8203520080327024738   psa-appvault-phpbook=1.50-8203220080327024809   psa-appvault-phpbugtracker=1.19-8203820080416050605   psa-appvault-phpdig=1.85-8203120080327024817   psa-appvault-phpmoney=1.3-8204320080327024822   psa-appvault-phpmyfamily=1.4.1-8203420080327024828   psa-appvault-phpmyvisites=2.3-8202820080327024834   psa-appvault-phprojekt=5.2-8200820080327024849   psa-appvault-phpsurveyor=0.98-8204320080327024905   psa-appvault-phpwebsite=0.10.2-8203420080327024918   psa-appvault-phpwiki=1.3.11-8204320080327024942   psa-appvault-pinnacle-cart=3.5.2-82059720080408070143   psa-appvault-plog=1.0-8203620080327025002   psa-appvault-pmachinefree=2.4-8203520080327025015   psa-appvault-postnuke=0.761a-8205620080327025030   psa-appvault-ray=3.0.0-8201220080412085531   psa-appvault-serendipity=1.1.2-8203020080327035434   psa-appvault-siteframe=3.2.2-8202920080327035503   psa-appvault-smf=1.1.2-8203320080327035512   psa-appvault-socialware=1.0-8200120080404001947   psa-appvault-ssm=1.0-8203720080327035522   psa-appvault-sugarcrm=5.0.0-8201220080327035551   psa-appvault-supportcenter=2.5.2-8200820080327035928   psa-appvault-supportdesk=3.0-8200120080404002110   psa-appvault-tellme=1.2-8202720080327035955   psa-appvault-tikiwiki=1.9.7-8203920080327040016   psa-appvault-tutos=1.88-8203820080327040120   psa-appvault-typo3=4.0-8202020080424050531   psa-appvault-uebimiau=2.7.8-8203720080327040218   psa-appvault-updates=9.3.0-ubuntu8.04.build93091230.07   psa-appvault-vivvocms=4.0.0-8200720080327040225   psa-appvault-webcalendar=1.0.5-8201020080327040236   psa-appvault-webshopmanager=2.0-8203120080327040241   psa-appvault-wordpress=2.3.3-8200520080412062207   psa-appvault-xoops=2.2-8204820080327040255   psa-appvault-xrms=1.19-8203120080415030843   psa-appvault-xtcommerce=3.0.4-8200920080327040328   psa-api-rpc=9.3.0-ubuntu8.04.build93091230.07   psa-migration-agents=9.3.0-ubuntu8.04.build93091230.07   psa-migration-manager=9.3.0-ubuntu8.04.build93091230.07   sb-publish=3.0.1-0.97008 plesk-billing=6.0.4-20090625.11   psa-tomcat-configurator=9.3.0-ubuntu8.04.build93091230.07   psa-rubyrails-configurator=1.1.6-ubuntu8.04.build93091230.07   psa-firewall=1.0.1-ubuntu8.04.build93091230.07   psa-vpn=1.0.1-ubuntu8.04.build93091230.07   psa-fileserver=1.0.0-ubuntu8.04.build93091230.07 sshterm=0.2.2-9.278624   psa-watchdog=2.0.3-ubuntu8.04.build93091230.07   psa-cs-gs=2.0.0-ubuntu8.04.build93091230.07   psa-bf1942=1.0.0-ubuntu8.04.build93091230.07   psa-bf2=1.0.0-ubuntu8.04.build93091230.07   psa-mailman-configurator=9.3.0-ubuntu8.04.build93091230.07 mailman   psa-spamassassin=9.3.0-ubuntu8.04.build93091230.07   psa-backup-manager=9.3.0-ubuntu8.04.build93091230.07   psa-ftputil=1:2.1.1-0.98221 psa-atis=1.0-50   psa-locale-de-de=9.3.0-2009121410 psa-locale-ja-jp=9.3.0-2009121410   psa-locale-es-es=9.3.0-2009121410 psa-locale-ru-ru=9.3.0-2009121410   psa-locale-fr-fr=9.3.0-2009121410 psa-locale-it-it=9.3.0-2009121410   psa-locale-zh-cn=9.3.0-2009121410 psa-locale-zh-tw=9.3.0-2009121410   psa-locale-nl-nl=9.3.0-2009121410   psa-horde=3.1.7-ubuntu8.04.build93091230.07   psa-imp=4.1.6-ubuntu8.04.build93091230.07   psa-ingo=1.1.5-ubuntu8.04.build93091230.07   psa-kronolith=2.1.8-ubuntu8.04.build93091230.07   psa-mimp=1.0.2-ubuntu8.04.build93091230.07   psa-mnemo=2.1.2-ubuntu8.04.build93091230.07   psa-passwd=3.0.1-ubuntu8.04.build93091230.07   psa-turba=2.1.7-ubuntu8.04.build93091230.07   psa-atmail=1:1.02-ubuntu8.04.build93091230.07 
 add to install list pwgen-2.06-1
 add to install list awstats-6.7.dfsg-1ubuntu0.1
 add to install list php5-common-5.2.4-2ubuntu5.11
 add to install list php5-cgi-5.2.4-2ubuntu5.11
 add to install list php5-cli-5.2.4-2ubuntu5.11
 add to install list libapache2-mod-php5-5.2.4-2ubuntu5.11
 add to install list php5-curl-5.2.4-2ubuntu5.11
 add to install list libt1-5-5.1.1-5
 add to install list php5-gd-5.2.4-2ubuntu5.11
 add to install list php5-imap-5.2.3-0ubuntu3.1
 add to install list php5-mysql-5.2.4-2ubuntu5.11
 add to install list php5-xsl-5.2.4-2ubuntu5.11
 add to install list libdb4.5-4.5.20-11
 add to install list libgeoip1-1.4.4.dfsg-1
 add to install list webalizer-2.01.10-32.1
 add to install list sw-sso-2.2-r3488
 add to install list libruby-4.1
 add to install list liberb-ruby-4.1
 add to install list libredcloth-ruby1.8-3.0.99.0.svn.20060519-1
 add to install list libbreakpoint-ruby1.8-0.5.1-2
 add to install list libcmdparse2-ruby1.8-2.0.2-2
 add to install list libdaemons-ruby1.8-1.0.9-1
 add to install list libreadline-ruby1.8-1.8.6.111-2ubuntu1.3
 add to install list irb1.8-1.8.6.111-2ubuntu1.3
 add to install list rdoc1.8-1.8.6.111-2ubuntu1.3
 add to install list libopenssl-ruby1.8-1.8.6.111-2ubuntu1.3
 add to install list libgems-ruby1.8-0.9.4-4
 add to install list liblog4r-ruby1.8-1.0.5-6
 add to install list libmmap-ruby1.8-0.2.6-2
 add to install list libncurses-ruby1.8-1.1-2
 add to install list libruby1.8-extras-0.4
 add to install list libmysql-ruby1.8-2.7.4-1
 add to install list rake-0.8.1-3
 add to install list rdoc-4.1
 add to install list rails-2.0.2-1ubuntu1
 add to install list sun-java6-jdk-6-17-0ubuntu1.8.04
 add to install list libapache2-mod-jk-1:1.2.25-2
 add to install list libjaxp1.3-java-1.3.04-2
 add to install list libxerces2-java-2.9.0-1
 add to install list ant-1.7.0-3
 add to install list libcommons-collections3-java-3.1a-3.1
 add to install list libcommons-pool-java-1.3-1
 add to install list libcommons-collections-java-2.1.1-8
 add to install list libcommons-dbcp-java-1.2.2-1
 add to install list libservlet2.4-java-5.0.30-6ubuntu1
 add to install list libcommons-el-java-1.0-4
 add to install list libservlet2.3-java-4.0-10
 add to install list libcommons-logging-java-1.1-1ubuntu1
 add to install list libcommons-launcher-java-1.1-3
 add to install list libcommons-beanutils-java-1.8.0~beta-1
 add to install list libcommons-digester-java-1.8-1
 add to install list libcommons-modeler-java-2.0.1-4
 add to install list libtomcat5.5-java-5.5.25-5ubuntu1.2
 add to install list libcommons-daemon-java-1.0.2~svn20061127-6
 add to install list jsvc-1.0.2~svn20061127-6
 add to install list libecj-java-3.3.0+0728-5
 add to install list tomcat5.5-5.5.25-5ubuntu1.2
 add to install list libcommons-io-java-1.3.2-2
 add to install list libcommons-fileupload-java-1.2-2
 add to install list liboro-java-2.0.8a-3
 add to install list libcommons-validator-java-1:1.3.1-1
 add to install list libstruts1.2-java-1.2.9-3
 add to install list tomcat5.5-admin-5.5.25-5ubuntu1.2
 add to install list tomcat5.5-webapps-5.5.25-5ubuntu1.2
 add to install list libboost-program-options1.34.1-1.34.1-4ubuntu3
 add to install list libboost-regex1.34.1-1.34.1-4ubuntu3
 add to install list libfcgi0ldbl-2.4.0-7
 add to install list libfcgi-ruby1.8-0.8.7-4build1
 add to install list libtimedate-perl-1.1600-9
 add to install list php5-5.2.4-2ubuntu5.11
 add to install list php5-ioncube-loader-3.3-ubn804.build08052012
 add to install list php5-sqlite-5.2.4-2ubuntu5.11
Check package set before installation
The following packages will be installed because they are required by   the packages you selected for installation: 
Installing packages
Need to install java, set default selections for j2re1.4 and j2sdk1.4
Execute command debconf-set-selections /tmp/autoinstaller3_debconf_answ
Execute command DEBIAN_FRONTEND=noninteractive LANG=C apt-get   --assume-yes --show-upgraded --purge --list-cleanup --no-reinstall -o   Dpkg::options::=--force-confdef -o Dpkg::options::=--force-confold -o   APT::Get::AllowUnauthenticated=true -t 'hardy*' install   libpam-plesk=9.3.0-ubuntu8.04.build93091230.07   plesk-skins=9.3.0-0.287499 psa=9.3.0-ubuntu8.04.build93091230.07   psa-api=9.3.0-ubuntu8.04.build93091230.07   psa-awstats-configurator=1.0.0-ubuntu8.04.build93091230.07   psa-proftpd=1.3.1-ubuntu8.04.build93091230.07   psa-proftpd-inetd=1.3.1-ubuntu8.04.build93091230.07   psa-updates=9.3.0-ubuntu8.04.build93091230.07   psa-autoinstaller=3.5.0-090817.16 psa-php5-configurator   psa-appvault-advancedpoll=2.03-8203720080327022632   psa-appvault-anyinventory=2.0-8202820080327022636   psa-appvault-articlepublisher=1.0-8200920080327022644   psa-appvault-autoindex=2.2.4-8200220080327022653   psa-appvault-avactis=1.8.1-8200720080327022715   psa-appvault-b2evolution=0.9.0.12-8203020080327022753   psa-appvault-bbclone=0.49-8200520080820033040   psa-appvault-brim=2.0.0-8203120080327022831   psa-appvault-coppermine=1.4.16-8200220080327022857   psa-appvault-cs-cart=1.3.5-8201220080327022957   psa-appvault-cslh=2.14.5-8200220080327023118   psa-appvault-cubecart=4.2.0-8200220080327023133   psa-appvault-docfaq=1.71-8203720080327023148   psa-appvault-dolphin=6.0.0-8201020080327023206   psa-appvault-drupal=6.1-8200320080327023245   psa-appvault-easybiller=1.0-8200120080404001639   psa-appvault-easysnaps=2.0-8200120080404001700   psa-appvault-egroupware=1.4.002-8201220080327023358   psa-appvault-emuwebmail=7.0.1-8200720080327023522   psa-appvault-eswap=1.0-8200220080404001727   psa-appvault-gallery=2.2-8201720080327023726   psa-appvault-geeklog=1.4.1-8200320080327024040   psa-appvault-gtchat=0.93-8003020080327024110   psa-appvault-helpcenterlive=2.1.5-8200220080327024115   psa-appvault-joomla=1.5.1-8200720080405023108   psa-appvault-knowledgetreeoss=3.4.5-8200820080327024234   psa-appvault-mailer=6.3-8200420080609232516   psa-appvault-mambo=4.6.2-8201520080327024329   psa-appvault-mantis=1.1.1-8200320080426054935   psa-appvault-mediawiki=1.11.0-8200920080327024423   psa-appvault-merchant=5.3-8003020080416013305   psa-appvault-moodle=1.8-8202920080327024531   psa-appvault-movabletype=4.0-8201520080415002955   psa-appvault-multicart=2.0-8200120080404001742   psa-appvault-myorgbook=2.8-8202720080327024652   psa-appvault-noahclass=1.3-8205520080327024657   psa-appvault-nucleus=3.21-8203220080327024701   psa-appvault-onebiz=8.0-8200120080405021240   psa-appvault-openbiblio=0.5-8204720080327024706   psa-appvault-oscommerce=2.2ms2-8206120080327024714   psa-appvault-osticket=1.3.0-8203320080327024721   psa-appvault-owl=0.80-8203620080327024726   psa-appvault-phpads=2.0.8-8203520080327024738   psa-appvault-phpbook=1.50-8203220080327024809   psa-appvault-phpbugtracker=1.19-8203820080416050605   psa-appvault-phpdig=1.85-8203120080327024817   psa-appvault-phpmoney=1.3-8204320080327024822   psa-appvault-phpmyfamily=1.4.1-8203420080327024828   psa-appvault-phpmyvisites=2.3-8202820080327024834   psa-appvault-phprojekt=5.2-8200820080327024849   psa-appvault-phpsurveyor=0.98-8204320080327024905   psa-appvault-phpwebsite=0.10.2-8203420080327024918   psa-appvault-phpwiki=1.3.11-8204320080327024942   psa-appvault-pinnacle-cart=3.5.2-82059720080408070143   psa-appvault-plog=1.0-8203620080327025002   psa-appvault-pmachinefree=2.4-8203520080327025015   psa-appvault-postnuke=0.761a-8205620080327025030   psa-appvault-ray=3.0.0-8201220080412085531   psa-appvault-serendipity=1.1.2-8203020080327035434   psa-appvault-siteframe=3.2.2-8202920080327035503   psa-appvault-smf=1.1.2-8203320080327035512   psa-appvault-socialware=1.0-8200120080404001947   psa-appvault-ssm=1.0-8203720080327035522   psa-appvault-sugarcrm=5.0.0-8201220080327035551   psa-appvault-supportcenter=2.5.2-8200820080327035928   psa-appvault-supportdesk=3.0-8200120080404002110   psa-appvault-tellme=1.2-8202720080327035955   psa-appvault-tikiwiki=1.9.7-8203920080327040016   psa-appvault-tutos=1.88-8203820080327040120   psa-appvault-typo3=4.0-8202020080424050531   psa-appvault-uebimiau=2.7.8-8203720080327040218   psa-appvault-updates=9.3.0-ubuntu8.04.build93091230.07   psa-appvault-vivvocms=4.0.0-8200720080327040225   psa-appvault-webcalendar=1.0.5-8201020080327040236   psa-appvault-webshopmanager=2.0-8203120080327040241   psa-appvault-wordpress=2.3.3-8200520080412062207   psa-appvault-xoops=2.2-8204820080327040255   psa-appvault-xrms=1.19-8203120080415030843   psa-appvault-xtcommerce=3.0.4-8200920080327040328   psa-api-rpc=9.3.0-ubuntu8.04.build93091230.07   psa-migration-agents=9.3.0-ubuntu8.04.build93091230.07   psa-migration-manager=9.3.0-ubuntu8.04.build93091230.07   sb-publish=3.0.1-0.97008 plesk-billing=6.0.4-20090625.11   psa-tomcat-configurator=9.3.0-ubuntu8.04.build93091230.07   psa-rubyrails-configurator=1.1.6-ubuntu8.04.build93091230.07   psa-firewall=1.0.1-ubuntu8.04.build93091230.07   psa-vpn=1.0.1-ubuntu8.04.build93091230.07   psa-fileserver=1.0.0-ubuntu8.04.build93091230.07 sshterm=0.2.2-9.278624   psa-watchdog=2.0.3-ubuntu8.04.build93091230.07   psa-cs-gs=2.0.0-ubuntu8.04.build93091230.07   psa-bf1942=1.0.0-ubuntu8.04.build93091230.07   psa-bf2=1.0.0-ubuntu8.04.build93091230.07   psa-mailman-configurator=9.3.0-ubuntu8.04.build93091230.07 mailman   psa-spamassassin=9.3.0-ubuntu8.04.build93091230.07   psa-backup-manager=9.3.0-ubuntu8.04.build93091230.07   psa-ftputil=1:2.1.1-0.98221 psa-atis=1.0-50   psa-locale-de-de=9.3.0-2009121410 psa-locale-ja-jp=9.3.0-2009121410   psa-locale-es-es=9.3.0-2009121410 psa-locale-ru-ru=9.3.0-2009121410   psa-locale-fr-fr=9.3.0-2009121410 psa-locale-it-it=9.3.0-2009121410   psa-locale-zh-cn=9.3.0-2009121410 psa-locale-zh-tw=9.3.0-2009121410   psa-locale-nl-nl=9.3.0-2009121410   psa-horde=3.1.7-ubuntu8.04.build93091230.07   psa-imp=4.1.6-ubuntu8.04.build93091230.07   psa-ingo=1.1.5-ubuntu8.04.build93091230.07   psa-kronolith=2.1.8-ubuntu8.04.build93091230.07   psa-mimp=1.0.2-ubuntu8.04.build93091230.07   psa-mnemo=2.1.2-ubuntu8.04.build93091230.07   psa-passwd=3.0.1-ubuntu8.04.build93091230.07   psa-turba=2.1.7-ubuntu8.04.build93091230.07   psa-atmail=1:1.02-ubuntu8.04.build93091230.07 pwgen awstats php5-common   php5-cgi php5-cli libapache2-mod-php5 php5-curl libt1-5 php5-gd   php5-imap php5-mysql php5-xsl libdb4.5 libgeoip1 webalizer sw-sso   libruby liberb-ruby libredcloth-ruby1.8 libbreakpoint-ruby1.8   libcmdparse2-ruby1.8 libdaemons-ruby1.8 libreadline-ruby1.8 irb1.8   rdoc1.8 libopenssl-ruby1.8 libgems-ruby1.8 liblog4r-ruby1.8   libmmap-ruby1.8 libncurses-ruby1.8 libruby1.8-extras libmysql-ruby1.8   rake rdoc rails sun-java6-jdk libapache2-mod-jk libjaxp1.3-java   libxerces2-java ant libcommons-collections3-java libcommons-pool-java   libcommons-collections-java libcommons-dbcp-java libservlet2.4-java   libcommons-el-java libservlet2.3-java libcommons-logging-java   libcommons-launcher-java libcommons-beanutils-java   libcommons-digester-java libcommons-modeler-java libtomcat5.5-java   libcommons-daemon-java jsvc libecj-java tomcat5.5 libcommons-io-java   libcommons-fileupload-java liboro-java libcommons-validator-java   libstruts1.2-java tomcat5.5-admin tomcat5.5-webapps   libboost-program-options1.34.1 libboost-regex1.34.1 libfcgi0ldbl   libfcgi-ruby1.8 libtimedate-perl php5 php5-ioncube-loader php5-sqlite 
Reading package lists...
Building dependency tree...
Reading state information...
Suggested packages:
 ant-doc libgeo-ipfree-perl libapache-mod-jk-doc php-pear
 libcommons-beanutils-java-doc libcommons-collections3-java-doc
 libcommons-io-java-doc liblogkit-java libavalon-framework-java   classpath-doc
 ecj geoip-bin libservlet2.4-java-gcj libxerces2-java-doc listadmin lynx
 graphviz openjdk-6-doc sun-java6-demo sun-java6-source
Recommended packages:
 ant-optional ant-gcj libnet-xwhois-perl libecj-java-gcj rubygems
 libjaxp1.3-java-gcj libxerces2-java-gcj irb libmocha-ruby1.8
The following NEW packages will be installed:
 ant awstats irb1.8 jsvc libapache2-mod-jk libapache2-mod-php5
 libboost-program-options1.34.1 libboost-regex1.34.1   libbreakpoint-ruby1.8
 libcmdparse2-ruby1.8 libcommons-beanutils-java   libcommons-collections-java
 libcommons-collections3-java libcommons-daemon-java   libcommons-dbcp-java
 libcommons-digester-java libcommons-el-java libcommons-fileupload-java
 libcommons-io-java libcommons-launcher-java libcommons-logging-java
 libcommons-modeler-java libcommons-pool-java libcommons-validator-java
 libdaemons-ruby1.8 libdb4.5 libecj-java liberb-ruby libfcgi-ruby1.8
 libfcgi0ldbl libgems-ruby1.8 libgeoip1 libjaxp1.3-java liblog4r-ruby1.8
 libmmap-ruby1.8 libmysql-ruby1.8 libncurses-ruby1.8 libopenssl-ruby1.8
 liboro-java libpam-plesk libreadline-ruby1.8 libredcloth-ruby1.8   libruby
 libruby1.8-extras libservlet2.3-java libservlet2.4-java   libstruts1.2-java
 libt1-5 libtimedate-perl libtomcat5.5-java libxerces2-java mailman php5
 php5-cgi php5-cli php5-common php5-curl php5-gd php5-imap
 php5-ioncube-loader php5-mysql php5-sqlite php5-xsl plesk-billing
 plesk-skins psa psa-api psa-api-rpc psa-appvault-advancedpoll
 psa-appvault-anyinventory psa-appvault-articlepublisher
 psa-appvault-autoindex psa-appvault-avactis psa-appvault-b2evolution
 psa-appvault-bbclone psa-appvault-brim psa-appvault-coppermine
 psa-appvault-cs-cart psa-appvault-cslh psa-appvault-cubecart
 psa-appvault-docfaq psa-appvault-dolphin psa-appvault-drupal
 psa-appvault-easybiller psa-appvault-easysnaps psa-appvault-egroupware
 psa-appvault-emuwebmail psa-appvault-eswap psa-appvault-gallery
 psa-appvault-geeklog psa-appvault-gtchat psa-appvault-helpcenterlive
 psa-appvault-joomla psa-appvault-knowledgetreeoss psa-appvault-mailer
 psa-appvault-mambo psa-appvault-mantis psa-appvault-mediawiki
 psa-appvault-merchant psa-appvault-moodle psa-appvault-movabletype
 psa-appvault-multicart psa-appvault-myorgbook psa-appvault-noahclass
 psa-appvault-nucleus psa-appvault-onebiz psa-appvault-openbiblio
 psa-appvault-oscommerce psa-appvault-osticket psa-appvault-owl
 psa-appvault-phpads psa-appvault-phpbook psa-appvault-phpbugtracker
 psa-appvault-phpdig psa-appvault-phpmoney psa-appvault-phpmyfamily
 psa-appvault-phpmyvisites psa-appvault-phprojekt   psa-appvault-phpsurveyor
 psa-appvault-phpwebsite psa-appvault-phpwiki psa-appvault-pinnacle-cart
 psa-appvault-plog psa-appvault-pmachinefree psa-appvault-postnuke
 psa-appvault-ray psa-appvault-serendipity psa-appvault-siteframe
 psa-appvault-smf psa-appvault-socialware psa-appvault-ssm
 psa-appvault-sugarcrm psa-appvault-supportcenter   psa-appvault-supportdesk
 psa-appvault-tellme psa-appvault-tikiwiki psa-appvault-tutos
 psa-appvault-typo3 psa-appvault-uebimiau psa-appvault-updates
 psa-appvault-vivvocms psa-appvault-webcalendar   psa-appvault-webshopmanager
 psa-appvault-wordpress psa-appvault-xoops psa-appvault-xrms
 psa-appvault-xtcommerce psa-atis psa-atmail psa-autoinstaller
 psa-awstats-configurator psa-backup-manager psa-bf1942 psa-bf2   psa-cs-gs
 psa-fileserver psa-firewall psa-ftputil psa-horde psa-imp psa-ingo
 psa-kronolith psa-locale-de-de psa-locale-es-es psa-locale-fr-fr
 psa-locale-it-it psa-locale-ja-jp psa-locale-nl-nl psa-locale-ru-ru
 psa-locale-zh-cn psa-locale-zh-tw psa-mailman-configurator
 psa-migration-agents psa-migration-manager psa-mimp psa-mnemo   psa-passwd
 psa-php5-configurator psa-proftpd psa-proftpd-inetd
 psa-rubyrails-configurator psa-spamassassin psa-tomcat-configurator
 psa-turba psa-updates psa-vpn psa-watchdog pwgen rails rake rdoc   rdoc1.8
 sb-publish sshterm sun-java6-jdk sw-sso tomcat5.5 tomcat5.5-admin
 tomcat5.5-webapps webalizer
0 upgraded, 200 newly installed, 0 to remove and 0 not upgraded.
Need to get 34.2MB/644MB of archives.
After this operation, 2636MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
 pwgen mailman awstats libpam-plesk plesk-skins psa-api php5-common   php5-cgi
 php5-cli libapache2-mod-php5 php5-curl libt1-5 php5-gd php5-imap   php5-mysql
 php5-xsl psa-php5-configurator psa-proftpd psa-proftpd-inetd libdb4.5
 libgeoip1 webalizer psa sw-sso plesk-billing libruby liberb-ruby
 libredcloth-ruby1.8 libbreakpoint-ruby1.8 libcmdparse2-ruby1.8
 libdaemons-ruby1.8 libreadline-ruby1.8 irb1.8 rdoc1.8   libopenssl-ruby1.8
 libgems-ruby1.8 liblog4r-ruby1.8 libmmap-ruby1.8 libncurses-ruby1.8
 libruby1.8-extras libmysql-ruby1.8 rake rdoc rails sun-java6-jdk   psa-bf2
 psa-cs-gs libapache2-mod-jk libjaxp1.3-java libxerces2-java ant
 libcommons-collections3-java libcommons-pool-java
 libcommons-collections-java libcommons-dbcp-java libservlet2.4-java
 libcommons-el-java libservlet2.3-java libcommons-logging-java
 libcommons-launcher-java libcommons-beanutils-java   libcommons-digester-java
 libcommons-modeler-java libtomcat5.5-java libcommons-daemon-java jsvc
 libecj-java tomcat5.5 libcommons-io-java libcommons-fileupload-java
 liboro-java libcommons-validator-java libstruts1.2-java tomcat5.5-admin
 tomcat5.5-webapps psa-tomcat-configurator psa-watchdog
 libboost-program-options1.34.1 libboost-regex1.34.1 libfcgi0ldbl
 libfcgi-ruby1.8 libtimedate-perl php5 php5-ioncube-loader php5-sqlite
 psa-api-rpc psa-appvault-advancedpoll psa-appvault-anyinventory
 psa-appvault-articlepublisher psa-appvault-autoindex   psa-appvault-avactis
 psa-appvault-b2evolution psa-appvault-bbclone psa-appvault-brim
 psa-appvault-coppermine psa-appvault-cs-cart psa-appvault-cslh
 psa-appvault-cubecart psa-appvault-docfaq psa-appvault-dolphin
 psa-appvault-drupal psa-appvault-easybiller psa-appvault-easysnaps
 psa-appvault-egroupware psa-appvault-emuwebmail psa-appvault-eswap
 psa-appvault-gallery psa-appvault-geeklog psa-appvault-gtchat
 psa-appvault-helpcenterlive psa-appvault-joomla
 psa-appvault-knowledgetreeoss psa-appvault-mailer psa-appvault-mambo
 psa-appvault-mantis psa-appvault-mediawiki psa-appvault-merchant
 psa-appvault-moodle psa-appvault-movabletype psa-appvault-multicart
 psa-appvault-myorgbook psa-appvault-noahclass psa-appvault-nucleus
 psa-appvault-onebiz psa-appvault-openbiblio psa-appvault-oscommerce
 psa-appvault-osticket psa-appvault-owl psa-appvault-phpads
 psa-appvault-phpbook psa-appvault-phpbugtracker psa-appvault-phpdig
 psa-appvault-phpmoney psa-appvault-phpmyfamily   psa-appvault-phpmyvisites
 psa-appvault-phprojekt psa-appvault-phpsurveyor psa-appvault-phpwebsite
 psa-appvault-phpwiki psa-appvault-pinnacle-cart psa-appvault-plog
 psa-appvault-pmachinefree psa-appvault-postnuke psa-appvault-ray
 psa-appvault-serendipity psa-appvault-siteframe psa-appvault-smf
 psa-appvault-socialware psa-appvault-ssm psa-appvault-sugarcrm
 psa-appvault-supportcenter psa-appvault-supportdesk psa-appvault-tellme
 psa-appvault-tikiwiki psa-appvault-tutos psa-appvault-typo3
 psa-appvault-uebimiau psa-appvault-updates psa-appvault-vivvocms
 psa-appvault-webcalendar psa-appvault-webshopmanager   psa-appvault-wordpress
 psa-appvault-xoops psa-appvault-xrms psa-appvault-xtcommerce psa-atis
 psa-atmail psa-autoinstaller psa-awstats-configurator psa-ftputil
 psa-backup-manager psa-bf1942 psa-fileserver psa-firewall psa-horde   psa-imp
 psa-ingo psa-kronolith psa-locale-de-de psa-locale-es-es   psa-locale-fr-fr
 psa-locale-it-it psa-locale-ja-jp psa-locale-nl-nl psa-locale-ru-ru
 psa-locale-zh-cn psa-locale-zh-tw psa-mailman-configurator
 psa-migration-manager psa-migration-agents psa-mimp psa-mnemo   psa-passwd
 psa-rubyrails-configurator psa-spamassassin psa-turba psa-updates   psa-vpn
 sb-publish sshterm
Authentication warning overridden.
Get:1 [http://autoinstall.plesk.com]("http://autoinstall.plesk.com/")  hardy/all sw-sso 2.2-r3488 [687kB]
Get:2 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy/main pwgen 2.06-1 [19.5kB]
Get:3 [http://autoinstall.plesk.com]("http://autoinstall.plesk.com/")  hardy/all psa-autoinstaller  3.5.0-090817.16 [2020kB]
Get:4 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy-updates/multiverse  sun-java6-jdk 6-17-0ubuntu1.8.04 [18.7MB]
Get:5 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy/universe libapache2-mod-jk  1:1.2.25-2 [133kB]
Get:6 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy/main libjaxp1.3-java 1.3.04-2  [179kB]
Get:7 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy/main libxerces2-java 2.9.0-1  [1122kB]
Get:8 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy/main ant 1.7.0-3 [1281kB]
Get:9 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy/main  libcommons-collections3-java 3.1a-3.1 [581kB]
Get:10 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy/universe libcommons-pool-java  1.3-1 [128kB]
Get:11 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy/universe  libcommons-collections-java 2.1.1-8 [330kB]
Get:12 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy/universe libcommons-dbcp-java  1.2.2-1 [118kB]
Get:13 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy/main libservlet2.4-java  5.0.30-6ubuntu1 [143kB]
Get:14 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy/universe libcommons-el-java  1.0-4 [111kB]
Get:15 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy/main libservlet2.3-java 4.0-10  [253kB]
Get:16 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy/main libcommons-logging-java  1.1-1ubuntu1 [195kB]
Get:17 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy/universe  libcommons-launcher-java 1.1-3 [134kB]
Get:18 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy/main libcommons-beanutils-java  1.8.0~beta-1 [201kB]
Get:19 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy/universe  libcommons-digester-java 1.8-1 [387kB]
Get:20 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy/universe  libcommons-modeler-java 2.0.1-4 [122kB]
Get:21 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy-updates/universe  libtomcat5.5-java 5.5.25-5ubuntu1.2 [2424kB]
Get:22 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy/universe  libcommons-daemon-java 1.0.2~svn20061127-6 [38.9kB]
Get:23 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy/universe jsvc  1.0.2~svn20061127-6 [25.0kB]
Get:24 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy/main libecj-java 3.3.0+0728-5  [1158kB]
Get:25 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy-updates/universe tomcat5.5  5.5.25-5ubuntu1.2 [61.2kB]
Get:26 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy/universe libcommons-io-java  1.3.2-2 [85.9kB]
Get:27 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy/universe  libcommons-fileupload-java 1.2-2 [42.5kB]
Get:28 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy/main liboro-java 2.0.8a-3  [69.1kB]
Get:29 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy/universe  libcommons-validator-java 1:1.3.1-1 [137kB]
Get:30 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy/universe libstruts1.2-java  1.2.9-3 [672kB]
Get:31 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy-updates/universe  tomcat5.5-admin 5.5.25-5ubuntu1.2 [1137kB]
Get:32 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy-updates/universe  tomcat5.5-webapps 5.5.25-5ubuntu1.2 [1491kB]
Get:33 [http://de.archive.ubuntu.com]("http://de.archive.ubuntu.com/")  hardy/main libtimedate-perl 1.1600-9  [30.1kB]
Extracting templates from packages: 15%Extracting templates from   packages: 30%Extracting templates from packages: 45%Extracting  templates  from packages: 60%Extracting templates from packages:  75%Extracting  templates from packages: 90%Extracting templates from  packages: 100%
Preconfiguring packages ...
Fetched 34.2MB in 4s (8029kB/s)
Selecting previously deselected package pwgen.
(Reading database ... 138873 files and directories currently installed.)
Unpacking pwgen (from .../pwgen_2.06-1_amd64.deb) ...
Selecting previously deselected package mailman.
Unpacking mailman (from .../mailman_1%3a2.1.9-9ubuntu1_amd64.deb) ...
Selecting previously deselected package awstats.
Unpacking awstats (from .../awstats_6.7.dfsg-1ubuntu0.1_all.deb) ...
Selecting previously deselected package libpam-plesk.
Unpacking libpam-plesk (from   .../libpam-plesk_9.3.0-ubuntu8.04.build93091230.07_amd64.deb) ...
Selecting previously deselected package plesk-skins.
Unpacking plesk-skins (from .../plesk-skins_9.3.0-0.287499_all.deb) ...
Selecting previously deselected package psa-api.
Unpacking psa-api (from   .../psa-api_9.3.0-ubuntu8.04.build93091230.07_amd64.deb) ...
Selecting previously deselected package php5-common.
Unpacking php5-common (from .../php5-common_5.2.4-2ubuntu5.11_amd64.deb)   ...
Selecting previously deselected package php5-cgi.
Unpacking php5-cgi (from .../php5-cgi_5.2.4-2ubuntu5.11_amd64.deb) ...
Selecting previously deselected package php5-cli.
Unpacking php5-cli (from .../php5-cli_5.2.4-2ubuntu5.11_amd64.deb) ...
Selecting previously deselected package libapache2-mod-php5.
Unpacking libapache2-mod-php5 (from   .../libapache2-mod-php5_5.2.4-2ubuntu5.11_amd64.deb) ...
Selecting previously deselected package php5-curl.
Unpacking php5-curl (from .../php5-curl_5.2.4-2ubuntu5.11_amd64.deb) ...
Selecting previously deselected package libt1-5.
Unpacking libt1-5 (from .../libt1-5_5.1.1-5_amd64.deb) ...
Selecting previously deselected package php5-gd.
Unpacking php5-gd (from .../php5-gd_5.2.4-2ubuntu5.11_amd64.deb) ...
Selecting previously deselected package php5-imap.
Unpacking php5-imap (from .../php5-imap_5.2.3-0ubuntu3.1_amd64.deb) ...
Selecting previously deselected package php5-mysql.
Unpacking php5-mysql (from .../php5-mysql_5.2.4-2ubuntu5.11_amd64.deb)   ...
Selecting previously deselected package php5-xsl.
Unpacking php5-xsl (from .../php5-xsl_5.2.4-2ubuntu5.11_amd64.deb) ...
Setting up php5-common (5.2.4-2ubuntu5.11) ...
Setting up libapache2-mod-php5 (5.2.4-2ubuntu5.11) ...

Selecting previously deselected package psa-php5-configurator.
(Reading database ... 151084 files and directories currently installed.)
Unpacking psa-php5-configurator (from   .../psa-php5-configurator_1.5.1-ubuntu8.04.build93091230.07_all.deb)  ...
Selecting previously deselected package psa-proftpd.
Unpacking psa-proftpd (from   .../psa-proftpd_1.3.1-ubuntu8.04.build93091230.07_amd64.deb) ...
 Checking for the system groups and users necessary for ftp server...
 Checking for the group 'psaftp'...
 Group 'psaftp' already exists

 Checking for the user 'psaftp'...
 User 'psaftp' already exists

Selecting previously deselected package psa-proftpd-inetd.
Unpacking psa-proftpd-inetd (from   .../psa-proftpd-inetd_1.3.1-ubuntu8.04.build93091230.07_amd64.deb) ...
Selecting previously deselected package libdb4.5.
Unpacking libdb4.5 (from .../libdb4.5_4.5.20-11_amd64.deb) ...
Selecting previously deselected package libgeoip1.
Unpacking libgeoip1 (from .../libgeoip1_1.4.4.dfsg-1_amd64.deb) ...
Selecting previously deselected package webalizer.
Unpacking webalizer (from .../webalizer_2.01.10-32.1_amd64.deb) ...
Selecting previously deselected package psa.
Unpacking psa (from .../psa_9.3.0-ubuntu8.04.build93091230.07_amd64.deb)   ...


===> Checking for the necessary system accounts
 Checking for the system groups and users necessary for MySQL...
 Checking for the group 'mysql'...
 Group 'mysql' already exists

 Checking for the user 'mysql'...
 User 'mysql' already exists

 Checking for the system groups and users necessary for admin server...
 Checking for the group 'psaadm'...
 Group 'psaadm' already exists

 Checking for the user 'psaadm'...
 User 'psaadm' already exists

 Checking for the group 'psaadm'...
 Trying to add supplementary group 'psaadm' for user 'sw-cp-server'...   already there
 Checking for the group 'psaserv'...
 Group 'psaserv' already exists

 Checking for the group 'psaserv'...
 Trying to add supplementary group 'psaserv' for user 'www-data'...   already there
 Checking for the group 'psaserv'...
 Trying to add supplementary group 'psaserv' for user 'psaftp'...   already there
 Checking for the group 'psaserv'...
 Trying to add supplementary group 'psaserv' for user 'psaadm'...   already there
 Checking for the group 'psacln'...
 Group 'psacln' already exists

 Checking for the system groups and users necessary for Apache...
 Checking for the group 'www-data'...
 Group 'www-data' already exists

 Checking for the user 'www-data'...
 User 'www-data' already exists

 Checking that /opt/psa/bin/chrootsh registered as login shell...

Selecting previously deselected package sw-sso.
Unpacking sw-sso (from .../sw-sso_2.2-r3488_all.deb) ...
Setting up awstats (6.7.dfsg-1ubuntu0.1) ...

Setting up plesk-skins (9.3.0-0.287499) ...
Setting up psa-api (9.3.0-ubuntu8.04.build93091230.07) ...

Setting up php5-cgi (5.2.4-2ubuntu5.11) ...

Setting up php5-cli (5.2.4-2ubuntu5.11) ...

Setting up php5-curl (5.2.4-2ubuntu5.11) ...

Setting up libt1-5 (5.1.1-5) ...

Setting up php5-gd (5.2.4-2ubuntu5.11) ...

Setting up php5-imap (5.2.3-0ubuntu3.1) ...

Setting up php5-mysql (5.2.4-2ubuntu5.11) ...

Setting up php5-xsl (5.2.4-2ubuntu5.11) ...

Setting up psa-php5-configurator (1.5.1-ubuntu8.04.build93091230.07) ...
===> configuring php5 using /etc/php5/apache2/php.ini file
 Trying to set memory limit to 32M... done
 Trying to add '.' to 'include_path'... nothing to be done
done
 Trying to set 'short_open_tag' to On... done
 Trying to set 'file_uploads' to On... done
 Trying to set 'safe_mode' to On... done
===> configuring php5 using /etc/php5/cli/php.ini file
 Trying to set memory limit to 32M... done
 Trying to add '.' to 'include_path'... nothing to be done
done
 Trying to set 'short_open_tag' to On... done
 Trying to set 'file_uploads' to On... done
 Trying to set 'safe_mode' to On... done
===> configuring php5 using /etc/php5/cgi/php.ini file
 Trying to set memory limit to 32M... done
 Trying to add '.' to 'include_path'... nothing to be done
done
 Trying to set 'short_open_tag' to On... done
 Trying to set 'file_uploads' to On... done
 Trying to set 'safe_mode' to On... done
This module is already enabled!

Setting up psa-proftpd (1.3.1-ubuntu8.04.build93091230.07) ...
 Trying to register service xinetd... using /usr/sbin/update-rc.d
 System startup links for /etc/init.d/xinetd already exist.
done
 Trying to restart service xinetd... * Stopping internet superserver   xinetd [180G [174G[ OK ]
 * Starting internet superserver xinetd [180G [174G[ OK ]
done
 Trying to restart service xinetd... * Stopping internet superserver   xinetd [180G [174G[ OK ]
 * Starting internet superserver xinetd [180G [174G[ OK ]
done

Setting up psa-proftpd-inetd (1.3.1-ubuntu8.04.build93091230.07) ...
 Trying to register service xinetd... using /usr/sbin/update-rc.d
 System startup links for /etc/init.d/xinetd already exist.
done
 Trying to restart service xinetd... * Stopping internet superserver   xinetd [180G [174G[ OK ]
 * Starting internet superserver xinetd [180G [174G[ OK ]
done

Setting up libdb4.5 (4.5.20-11) ...
Setting up libgeoip1 (1.4.4.dfsg-1) ...

Setting up webalizer (2.01.10-32.1) ...

Setting up sw-sso (2.2-r3488) ...

DB file already exists. Let's check for upgrade
Restarting SWsoft control panels server... stale pidfile. ok

Setting up psa (9.3.0-ubuntu8.04.build93091230.07) ...
 Trying to register service xinetd... using /usr/sbin/update-rc.d
 System startup links for /etc/init.d/xinetd already exist.
done
 Trying to restart service xinetd... * Stopping internet superserver   xinetd [180G [174G[ OK ]
 * Starting internet superserver xinetd [180G [174G[ OK ]
done
Setting the default locale

ERROR while trying to set up default locale: cannot read   '/opt/psa/admin/htdocs/locales/default'
Check the error reason(see log file:   /tmp/psa_9.3.0_ubuntu8.04.build93091230.07_upgrade.100320.23.59.log),   fix and try again

Aborting...

dpkg: error processing psa (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libpam-plesk:
 libpam-plesk depends on psa-9.3.0; however:
 Package psa-9.3.0 is not installed.
 Package psa which provides psa-9.3.0 is not configured yet.
dpkg: error processing libpam-plesk (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 psa
 libpam-plesk
E: Sub-process /usr/bin/dpkg returned an error code (1)
ERROR: An error occurred on attempt to install packages.
Attention! Your software might be inoperable.
Please, contact product technical support.

```

---

### Post by FewG on 2010-03-21
any ideas? :KS

---

