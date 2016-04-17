
---- 
@title:Issue为谁开，branch君再来
---- 
这是一个真实的小故事。
虽然有人生来就懂得这个道理，也有人写一辈子代码也未必会明白，但是我相信更多的人要用整个职业生涯去体会这里的精髓。

\*\*故事概要
一个小程序猿（代号小Y）闲来无事，决定探索一个陌生的开源消息组件[ZeroMQ][1]，以图未来有一天可以为改变世界做出贡献，可是他遇到了一个installing的问题——所有问题中最低级的那种。
\*\*confiure failed ! make failed ! Fuck !


![基于Github的开源管理流程][image-1]

### Search & Open Issue
**Baidu.com \>\> Google \>\> issues (正确的姿势应该反过来！**
![issue filter][image-2]
常规首发看起来，没什么收获，万般无奈之下，小Y操着瘪犊子英文勇敢地open 了一个[Issue][2]。

### Disscution
\`\`\`
configure log
make log
balala balala  
\`\`\`

\*\*其实此刻小Y是不抱什么希望的。
\*\*I can’t believe !!
\*\*地球另一头,正在喝着咖啡的同行居然回复了！
Hi,
Does the same problem happen with libzmq master from this repository?
I've got no way to test it, but in theory at least the "select" method should work.
Maybe it's the lack of #include \<time.h\> in acinclude.m4, line 871? If I'm reading it correctly, the SunOS 5.1 manpage says it should be used: http://www.unix.com/man-page/sunos/3c/select/


### Revert

\`\`\`\`
Could you please run: git revert b6080a798
\`\`\`\`
经过一番勾搭，以及小Y诚恳无耻的描述，对方似乎开始怀疑自己啦，开始建议切换代码版本试试。\*\*有戏！


### New branch for Me !
\*** Surprise!! 他们居然为我开了一个branch(分支)** Could you please try from this branch of mine?
\`\`\` 
git remote add bluca https://github.com/bluca/libzmq.git
git fetch bluca
git checkout solaris\_fixes
\`\`\`

I've got a couple of changes that should fix that problem and the one caused by the commit you reverted. But I have no Solaris box to test them (trying to setup a VM with Solaris 10 x86) so I wanted to be sure it works before sending them. Thanks!

### Pull request & Merge
\`\`\`\`
\`\`\`\`

![][image-3]
---- 
---- 
![][image-4]

### Contributions that are counted
\`\`\`\`

\`\`\`\`
![][image-5]

* Issues and pull requests

Issues and pull requests will appear on your contributions graph if they meet both of these conditions:
They were opened within the past year.
They were opened in a standalone repository, not a fork.
* Commits
Commits will appear on your contributions graph if they meet all of the following conditions:
The commits were made within the past year.
The email address used for the commits is associated with your GitHub account.
The commits were made in a standalone repository, not a fork.
The commits were made:
In the repository's default branch (usually master)
In the gh-pages branch (for repositories with Project Pages sites)
In addition, at least one of the following must be true:
You are a collaborator on the repository or are a member of the organization that owns the repository.
You have forked the repository.
You have opened a pull request or issue in the repository.
You have starred the repository.

## 总结

[1]:	http://www.jianshu.com/collection/4bc170355af0
[2]:	https://github.com/zeromq/libzmq/issues/1866

[image-1]:	20160417-zmq-solaris-fix.png
[image-2]:	20160417-issue-filter.png
[image-3]:	20160417-fix-4.png
[image-4]:	20160417-fix-3.png
[image-5]:	20160417-contribution-1.png