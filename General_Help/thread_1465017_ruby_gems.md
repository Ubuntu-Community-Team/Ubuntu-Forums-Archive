---
title: "ruby gems"
date: 2010-04-29
forum: General Help
---

### Post by A7med on 2010-04-29
Hi , I wanted to install a similar application to text mate or E on windows and I found this 
[http://redcareditor.com/](http://redcareditor.com/)  which seems nice so I installed ruby gems and it was installed correctly but now I don't know how gems run ? by typing their names in console ? because that doesn't work . 
Apologize my n00bish question but i did some googling and looked through their FAQs which is all about installing and developing and managing gems but nothing is written about how to open my gem .

I miss .exe files :confused: .

That's the output of typing redcar in terminal
```
Redcar 0.3.4 ( i486-linux )                        
java  -Xmx500m -Xss1024k -Djruby.memory.max=500m -Djruby.stack.max=1024k -cp "/usr/lib/ruby/gems/1.8/gems/redcar-0.3.4.3/lib/jruby-complete-1.4.0.jar" org.jruby.Main "/usr/lib/ruby/gems/1.8/gems/redcar-0.3.4.3/lib/redcar/../../bin/redcar"  --no-sub-jruby                                                      
Redcar 0.3.4 ( java )                                                        
SWT jar file required: /usr/lib/ruby/gems/1.8/gems/redcar-0.3.4.3/plugins/application_swt/vendor/swt/linux/swt.jar                                        
Error loading plugin: <Plugin application_swt 1.0 depends:[application>0] 0 files>                                                                        
  exit                                                                       
  /usr/lib/ruby/gems/1.8/gems/redcar-0.3.4.3/plugins/application_swt/lib/application_swt/swt_wrapper.rb:31:in `require'                                   
  file:/usr/lib/ruby/gems/1.8/gems/redcar-0.3.4.3/lib/jruby-complete-1.4.0.jar!/META-INF/jruby.home/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'                                                                  
  /usr/lib/ruby/gems/1.8/gems/redcar-0.3.4.3/plugins/application_swt/lib/application_swt.rb:4                                                             
  /usr/lib/ruby/gems/1.8/gems/redcar-0.3.4.3/plugins/application_swt/lib/application_swt.rb:31:in `require'                                               
  file:/usr/lib/ruby/gems/1.8/gems/redcar-0.3.4.3/lib/jruby-complete-1.4.0.jar!/META-INF/jruby.home/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'                                                                  
  /usr/lib/ruby/gems/1.8/gems/redcar-0.3.4.3/lib/plugin_manager/lib/plugin_manager/plugin_definition.rb:36:in `load'                                      
  /usr/lib/ruby/gems/1.8/gems/redcar-0.3.4.3/lib/plugin_manager/lib/plugin_manager/plugin_definition.rb:56:in `log_requires'                              
  /usr/lib/ruby/gems/1.8/gems/redcar-0.3.4.3/lib/plugin_manager/lib/plugin_manager/plugin_definition.rb:35:in `load'                                      
  /usr/lib/ruby/gems/1.8/gems/redcar-0.3.4.3/lib/plugin_manager/lib/plugin_manager.rb:49:in `load'                                                        
  /usr/lib/ruby/gems/1.8/gems/redcar-0.3.4.3/lib/redcar.rb:91:in `load'      
  /usr/lib/ruby/gems/1.8/gems/redcar-0.3.4.3/lib/redcar/../../bin/redcar:21  
Error loading plugin: <Plugin HTML View 0.3.2 depends:[core>0, application>0] 0 files>
  uninitialized constant Swt::Browser
  file:/usr/lib/ruby/gems/1.8/gems/redcar-0.3.4.3/lib/jruby-complete-1.4.0.jar!/META-INF/jruby.home/lib/ruby/site_ruby/shared/builtin/javasupport/core_ext/object.rb:120:in `const_missing'
  /usr/lib/ruby/gems/1.8/gems/redcar-0.3.4.3/plugins/html_view/lib/html_view.rb:24
  /usr/lib/ruby/gems/1.8/gems/redcar-0.3.4.3/plugins/html_view/lib/html_view.rb:31:in `require'
  file:/usr/lib/ruby/gems/1.8/gems/redcar-0.3.4.3/lib/jruby-complete-1.4.0.jar!/META-INF/jruby.home/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'
  /usr/lib/ruby/gems/1.8/gems/redcar-0.3.4.3/lib/plugin_manager/lib/plugin_manager/plugin_definition.rb:36:in `load'
  /usr/lib/ruby/gems/1.8/gems/redcar-0.3.4.3/lib/plugin_manager/lib/plugin_manager/plugin_definition.rb:56:in `log_requires'
  /usr/lib/ruby/gems/1.8/gems/redcar-0.3.4.3/lib/plugin_manager/lib/plugin_manager/plugin_definition.rb:35:in `load'
  /usr/lib/ruby/gems/1.8/gems/redcar-0.3.4.3/lib/plugin_manager/lib/plugin_manager.rb:49:in `load'
  /usr/lib/ruby/gems/1.8/gems/redcar-0.3.4.3/lib/redcar.rb:91:in `load'
  /usr/lib/ruby/gems/1.8/gems/redcar-0.3.4.3/lib/redcar/../../bin/redcar:21
There was an error loading plugins:
  * application_swt
  * HTML View
/usr/lib/ruby/gems/1.8/gems/redcar-0.3.4.3/lib/redcar.rb:100:in `const_missing': uninitialized constant Redcar::Top (NameError)
        from /usr/lib/ruby/gems/1.8/gems/redcar-0.3.4.3/lib/redcar/../../bin/redcar:22
```

---

### Post by A7med on 2010-04-29
bump

---

