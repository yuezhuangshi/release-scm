# release

## 命令

### 清理
```shell script
mvn release:clean
```

### 发布准备
1) 检测是否有未提交的代码
2) 检测是否有snapshot依赖
3) 修改工程的版本号为release版本(提示输入)
4) 为当前代码打上一个git的tag(提示输入),提交代码至远程仓库
5) 修改pom为下一个snapshot版本(输入提示),提交至远程仓库
这里一共提交了两次代码,第一次是 release 版本,第二次是 snapshot 版本
```shell script
mvn release:prepare
mvn release:prepare -DdryRun=true
```

### 发布
依赖于 release:prepare 阶段生成的release.properties文件,
执行 mvn deploy, 发包到远程仓库
```shell script
mvn release:perform
```

### 回滚
回滚改动
```shell script
release:rollback
```
