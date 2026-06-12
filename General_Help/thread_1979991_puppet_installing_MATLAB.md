---
title: "puppet installing MATLAB"
date: 2012-05-14
forum: General Help
---

### Post by MonserrateM on 2012-05-14
So I am new to puppet and have been reading through a user guide to get better acquainted with he program. As a result I have been able to get some programs to install (i.e. vim and apache2) using the pp files.

Now I have been trying to deploy matlab on my client but I keep getting an error:
Failed to apply catalog: 'wget [http://remoteserver/matlab64-2011b.tgz;](http://remoteserver/matlab64-2011b.tgz;) tar matlab64-2011b.tgz --directory /' is not qualified and no path was specified. Please qualify the command or specify a path.

I feel like I'm just not setting up the script correctly, so if some puppet master pro or at least someone who has had their puppet server/client working tell me if you see an issue with this script?

**In /etc/puppet/manifests/site.pp**

import 'nodes.pp'
$puppetserver = 'myserver'

**In /etc/puppet/manifests/nodes.pp  **

node 'myclient' {
  include matlab
}

**In /etc/puppet/modules/matlab/manifests/init.pp:**

class matlab {
   if $operatingsystem == 'ubuntu' {
        exec { "matlab":
            command => "wget [http://remoteserver/matlab64-2011b.tgz;](http://remoteserver/matlab64-2011b.tgz;) tar xzf matlab64-2011b.tgz --directory /",
            path    => "/usr/local/bin",
            creates => "/opt/matlab/7.13-r2010b/bin/matlab"
         }

        package { "matlab" :
            ensure  => latest
        }

   }

   file { "/opt/matlab/7.13-r2010b/toolbox/local/matlabrc.m":
        owner   => 'root',
        group   => 'root',
        source  => "puppet://$puppetserver/modules/matlab/files/opt/matlab/toolbox/local/matlabrc.m"
   }
}




What am I missing? :???:

---

