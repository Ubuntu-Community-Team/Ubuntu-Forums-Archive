---
title: "Openbravo-3.0 on Ubuntu 12.04"
date: 2012-04-30
forum: General Help
---

### Post by ipk1uk84 on 2012-04-30
Hi,

I have installed Ubuntu 12.04 and want to install Openbravo-3.0.

Having added the Openbravo-isv ppa for 11.10 (as a 12.04 version does not currently exist yet) I have tried to install both from the software centre and from the terminal.

Using either method I receive the following:

Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for ureadahead ...
Setting up openbravo-3 (3.0.r16013.MP-10-1oneiric1) ...
 * Initializing openbravo-postgresql database                                   Creating new cluster (configuration: /etc/postgresql/8.4/openbravo-3, data: /opt/OpenbravoERP-3.0/postgresql)...
Moving configuration file /opt/OpenbravoERP-3.0/postgresql/postgresql.conf to /etc/postgresql/8.4/openbravo-3...
Moving configuration file /opt/OpenbravoERP-3.0/postgresql/pg_hba.conf to /etc/postgresql/8.4/openbravo-3...
Moving configuration file /opt/OpenbravoERP-3.0/postgresql/pg_ident.conf to /etc/postgresql/8.4/openbravo-3...
Configuring postgresql.conf to use port 5932...
                                                                         [ OK ]
 * Starting openbravo-postgresql                                         [ OK ] 
Creating the Openbravo ERP database ...
Setting up Openbravo ERP ...
dpkg: error processing openbravo-3 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 openbravo-3
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have tried a variety of fixes from a variety of forums but with no success.

Does anybody have any suggestions/experience of getting Openbravo 3 working on Ubuntu 12.04?

Thanks

---

