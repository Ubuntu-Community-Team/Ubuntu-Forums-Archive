---
title: "Help With Gyazo."
date: 2011-02-08
forum: General Help
---

### Post by LoC Blood Red on 2011-02-08
Well I'm new to linux and I've hit a road block when installing Gyazo(A screen capping tool.)

I install imagemagick and ruby.
Open gedit and paste the code into it.

Code 

```
#!/usr/bin/env ruby 

# setting 
browser_cmd = 'firefox' 
clipboard_cmd = 'xclip' 
proxy_addr = nil 
proxy_port = nil 

require 'net/http' 

# get id 
idfile = ENV['HOME'] + "/.gyazo.id" 

id = '' 
if File.exist?(idfile) then 
  id = File.read(idfile).chomp 
end 

# capture png file 
tmpfile = "/tmp/image_upload#{$$}.png" 
imagefile = ARGV[0] 

if imagefile && File.exist?(imagefile) then 
  system "convert #{imagefile} #{tmpfile}" 
else 
  system "import #{tmpfile}" 
end 

if !File.exist?(tmpfile) then 
  exit 
end 

imagedata = File.read(tmpfile) 
File.delete(tmpfile) 

# upload 
boundary = '----BOUNDARYBOUNDARY----' 

HOST = 'gyazo.com' 
CGI = '/upload.cgi' 
UA   = 'Gyazo/1.0' 

data = <<EOF 
--#{boundary}\r 
content-disposition: form-data; name="id"\r 
\r 
#{id}\r 
--#{boundary}\r 
content-disposition: form-data; name="imagedata"; filename="gyazo.com"\r 
\r 
#{imagedata}\r 
--#{boundary}--\r 
EOF 

header ={ 
  'Content-Length' => data.length.to_s, 
  'Content-type' => "multipart/form-data; boundary=#{boundary}", 
  'User-Agent' => UA 
} 

Net::HTTP::Proxy(proxy_addr, proxy_port).start(HOST,80) {|http| 
  res = http.post(CGI,data,header) 
  url = res.response.to_ary[1] 
  puts url 
  if system "which #{clipboard_cmd} >/dev/null 2>&1" then 
    system "echo -n #{url} | #{clipboard_cmd}" 
  end 
  system "#{browser_cmd} #{url}" 

  # save id 
  newid = res.response['X-Gyazo-Id'] 
  if newid and newid != "" then 
    if !File.exist?(File.dirname(idfile)) then 
      Dir.mkdir(File.dirname(idfile)) 
    end 
    if File.exist?(idfile) then 
      File.rename(idfile, idfile+Time.new.strftime("_%Y%m%d%H%M%S.bak")) 
    end 
    File.open(idfile,"w").print(newid) 
  end 
}
```

I Then save it as Gyazo.rb and do chmod, but when I try to test it while using 'ruby Gyazo.rb'

It gives me the following error.

```
Gyazo.rb:81: can't find string "EOF" anywhere before EOF
Gyazo.rb:43: syntax error, unexpected $end, expecting tSTRING_CONTENT or tSTRING_DBEG or tSTRING_DVAR or tSTRING_END
data = <<EOF 

```

I know nothing about Ruby or anything dealing with this.

Any help would be appreciated.

---

### Post by LoC Blood Red on 2011-02-08
Anybody?

---

### Post by Captainhooba on 2011-04-02
Make sure you have ruby installed and change the extension to .sh and run that ;)

---

