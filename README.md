# React-native debug

## 1.react-native(0.54) TextInput 中文输入bug

[https://github.com/facebook/react-native/pull/18456/files ](https://github.com/facebook/react-native/pull/18456/files )
这个直接改library 里面的代码效果比上面好

## 2. RN本地存储数据持久化

   - [AsyncStorage](https://facebook.github.io/react-native/docs/asyncstorage.html)
   
   是一个简单的、异步的、持久化的Key-Value存储系统。优点：
   
   1）使用简单，常用的API同localstorage；
   
  （2）异步机制，带了成功失败回调，方便向业务靠拢；
  
  （3）目前有一个不错的[库](https://github.com/sunnylqm/react-native-storage)，对存储条数、过期时间等做了封装。
  
  存在问题：
  
  （1）Key-Value存储系统不好应对复杂数据处理（所以要考虑好需要存储的内容）；
  
  （2）存储上限的问题。
  
    react-native讨论存储上限的 [issues](https://github.com/facebook/react-native/issues/3387#issuecomment-148042923)，[中文](https://github.com/sunnylqm/react-native-storage/issues/111) 
    
    Android:
    
    默认的上限是6M，看源码,我们发现可以通过重写setMaximumSize的方式来扩大上限，代码类似如下：
    
    

    
    long size = 50L * 1024L * 1024L; // 50 MB 
    
com.facebook.react.modules.storage.ReactDatabaseSupplier.getInstance(getApplicationContext()).setMaximumSize(size);

    
    ios:
    
    
    On iOS, AsyncStorage is backed by native code that stores small values in a serialized dictionary and larger values in separate files.
    
    
    - [react-native-sqlite-storage](https://github.com/andpor/react-native-sqlite-storage)
    
    
    使用场景：需要复杂大量数据的处理
    
    
    
    
    - [Realm](https://realm.io)
    
    
    Realm是一个适应多平台，功能强大的数据库
    
