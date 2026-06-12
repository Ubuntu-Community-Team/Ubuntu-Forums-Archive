---
title: "SFTP User add script"
date: 2012-02-01
forum: General Help
---

### Post by extremal on 2012-02-01
Somewhere in the internet i found that script for CentOS and now it is interesting if someone can convert it into ubuntu

```
mkdir -p /root/bin
cat << EOF > /root/bin/hosting_user_add
#!/bin/sh
# "chown root.root"s are implied, but kept to be safe


if [ -z \$1 ];then
  echo "Usage: \$1 user1 [user2]"
  exit 1
fi

for username in "\$@";do
  read -p "Restrict \$username (make member of serv_sftponly)? [Y/n] " -t 60 -n 1 response
  echo
  if [ "\$response" == "n" ] || [ "\$response" == "N" ];then
    echo "*** Creating normal user \$username"
    useradd -G serv_sshall \$username
  else
    echo "*** Creating restricted user \$username"
    useradd -G serv_sftponly -s /sbin/nologin \$username
  fi
  chown \$username.apache /home/\$username
  chmod 710 /home/\$username
  
  # Set password
  passwd \$username
  
  # Initialize mail storage folder
  mkdir -m 0700 /home/\$username/mail
  chown \$username.\$username /home/\$username/mail
  
  # Initialize web folders
  mkdir -p -m 0755 /home/\$username/web
  chown root.root /home/\$username/web
  # Web: logs
  mkdir -p -m 0750 /home/\$username/web/logs
  chown root.\$username /home/\$username/web/logs
  # Web: offline/private storage
  mkdir -p -m 0755 /home/\$username/web/storage
  chown \$username.\$username /home/\$username/web/storage
  # Web: docroot
  mkdir -m 0755 /home/\$username/web/public_html
  ln -s public_html /home/\$username/web/www
  # make it so they can't remove the symlink
  chown -h root.root /home/\$username/web/www
  chown \$username.\$username /home/\$username/web/public_html
  # Web: PHP error log
  touch /home/\$username/web/php_error_log
  chown \$username.\$username /home/\$username/web/php_error_log
  chattr +u /home/\$username/web/php_error_log

  # Initialize session folder
  mkdir -m 0770 /var/lib/php/session/\$username
  chown root.\$username /var/lib/php/session/\$username

  # SSH: SFTP login
  ln -s ../../home/\$username/web /srv/sftp/\$username

  # SSH: Authorized keys dir
  mkdir -m 0700 /home/\$username/.ssh
  chown \$username.\$username /home/\$username/.ssh
  # Key description here
  echo "your_key_here" >> /home/\$username/.ssh/authorized_keys

  chmod 600 /home/\$username/.ssh/authorized_keys
  chown \$username.\$username /home/\$username/.ssh/authorized_keys
  restorecon -v -r /home/\$username
done
EOF
chmod +x /root/bin/hosting_user_add
```

I had changed it into

```
mkdir -p /root/bin
cat << EOF > /root/bin/hosting_user_add
#!/bin/sh
# "chown root.root"s are implied, but kept to be safe


if [ -z \$1 ];then
  echo "Usage: \$1 user1 [user2]"
  exit 1
fi

for username in "\$@";do
  read -p "Restrict \$username (make member of serv_sftponly)? [Y/n] " -t 60 -n 1 response
  echo
  if [ "\$response" == "n" ] || [ "\$response" == "N" ];then
    echo "*** Creating normal user \$username"
    useradd -G sshall \$username
  else
    echo "*** Creating restricted user \$username"
    useradd -G sftponly -s /sbin/nologin \$username
  fi
  chown \$username /home/\$username
  chmod 710 /home/\$username
  
  # Set password
  passwd \$username
  
  # Initialize web folders
  mkdir -p -m 0755 /home/\$username/web
  chown root.root /home/\$username/web
 
  # SSH: SFTP login
  ln -s ../../home/\$username/web /srv/sftp/\$username

  # SSH: Authorized keys dir
  mkdir -m 0700 /home/\$username/.ssh
  chown \$username.\$username /home/\$username/.ssh
  # Key description here
  echo "your_key_here" >> /home/\$username/.ssh/authorized_keys

  chmod 600 /home/\$username/.ssh/authorized_keys
  chown \$username.\$username /home/\$username/.ssh/authorized_keys
  restorecon -v -r /home/\$username
done
EOF
chmod +x /root/bin/hosting_user_add
```

For the reason that i dont have mail apache and others , i just need chrooted sftp with symlinks so users cant see .ssh directory with the keyfile

---

