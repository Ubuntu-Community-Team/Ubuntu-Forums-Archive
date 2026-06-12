---
title: "Ubuntu 8.04 64-bit server - MySQL does not have InnoDB engine"
date: 2010-01-26
forum: General Help
---

### Post by KayakJim on 2010-01-26
I have a server running Ubuntu 8.04 Hardy 64-bit server and just installed MySQL using the command
```
sudo apt-get install mysql-server mysql-client libmysqlclient15-dev
```

and everything appears the be running fine. I can access mysql from the command line and do everything else.

The only catch is that the InnoDB storage engine is not active even though I have the following settings in my /etc/mysql/my.cnf file:
```
innodb_buffer_pool_size = 200M
innodb_additional_mem_pool_size = 2M
innodb_data_file_path = ibdata1:50M:autoextend
innodb_log_file_size = 5M
innodb_log_buffer_size = 8M
```

Can anyone advise on what I need to do in order to be able to use the InnoDB storage engine?

---

### Post by KayakJim on 2010-01-28
Any ideas are welcome.

I am needing to install Magento which requires InnoDB tables but I cannot for the life of me figure out why my MySQL engine is not providing them.

---

