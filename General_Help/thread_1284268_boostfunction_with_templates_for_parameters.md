---
title: "boost::function with templates for parameters"
date: 2009-10-06
forum: General Help
---

### Post by programmine on 2009-10-06
I am using boost:functions and want to pass a Type which itself is using templates. From my knowledge this could look like this: 

template<typename VarType>  
boost::function<void (std::string, VarType)> UpdateShaderParameter; 

But the compiler throws two errors: 

error C2079: [..] uses undefined class 'boost::function<void(std::string,VarType)>' 
error C3857: [..] multiple template parameter lists are not allowed 

How can I use the boost function in this context? 
Thanks guys

---

