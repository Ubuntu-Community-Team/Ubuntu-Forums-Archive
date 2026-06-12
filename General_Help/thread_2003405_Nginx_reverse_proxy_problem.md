---
title: "Nginx reverse proxy problem"
date: 2012-06-14
forum: General Help
---

### Post by sphairos on 2012-06-14
Hi folks,

I wanted to use Nginx as reverse proxy for simple URL for Alfresco.

Usually for connecting to Alfresco URL look like this : 
http://<IP address>:8080/share 

What I want is :
http://<my_domain_name>

For this I tried to follow this steps : 
```

Install Nginx: 
# apt-get install nginx
 
- create a vhost configuration for the site
 # touch /etc/nginx/sites-available/<my_domain_name> 

- throw in the following basic configuration
 # vi /etc/nginx/sites-availale/<my_domain_name>
 
server {
 listen 80;
 server_name <my_domain_name>;
 access_log /var/log/nginx/access.log;
 error_log /var/log/nginx/error.log;
 
location / {
 proxy_pass http://localhost:8080;
 proxy_set_header X-Real-IP $remote_addr;
 proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
 proxy_set_header Host $http_host;
 }
 
location /alfresco {
 proxy_pass http://localhost:8080/alfresco;
 proxy_set_header X-Real-IP $remote_addr;
 proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
 proxy_set_header Host $http_host;
 }
 
location /share {
 proxy_pass http://localhost:8080/share;
 proxy_set_header X-Real-IP $remote_addr;
 proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
 proxy_set_header Host $http_host;
 }
 }
 
- symlink the config to enable vhost
 # ln -s /etc/nginx/site-availale/<my_domain_name> /etc/nginx/site-enabled/<my_domain_name>
 
- restart Nginx
 # /etc/init.d/nginx restart

```

But my small finger told me I must miss understand something because when I launch this http://<my_domain_name> I just go on nginx's page that say "Welcome to nginx!"

Thanks for your help

---

