---
layout: post
title: Flyweight
categories: 
 - DP
tags:
 - DP
---

* content
{:toc}

> 设计模式系列文章参考`GeekBand-李建忠`老师课堂内容整理。如有意购买该课程请访问网易云课堂。

## 动机

1. 在软件系统采用纯粹对象方案的问题在于大量细粒度的对象会很快充斥在系统中，从而带来很高的运行代价——主要指内存需求方面的代价。
2. 如何在避免大量细粒度对象问题的同时，让外部客户程序仍然能够透明地使用面向对象的方式来进行操作？




## 定义

	运用共享技术有效地支持大量细粒度的对象。

## 伪码

```c
class Font 
{
private:
	string key;

public:
	Font(const string& key) { }
};

class FontFactory
{
private:
	map<string, Font* > fontPool;
    
public:
	Font* GetFont(const string& key)
	{
		map<string,Font*>::iterator item = fontPool.find(key);

		if (item != footPool.end())
		{
			return fontPool[key];
		}
		else
		{
			Font* font = new Font(key);
			fontPool[key]= font;
			return font;
		}
	}
};
```

## 总结

1. 面向对象很好地解决了抽象性的问题，但是作为一个运行在机器中的程序实体，我们需要考虑对象的代价问题。Flyweight主要解决面向对象的代价问题，一般不触及面向对象的抽象性问题。
2. Flyweight采用对象共享的做法来降低系统中对象的个数，从而降低细粒度对象给系统带来的内存压力。在具体实现方面，要注意对象状态的处理。
3. 对象的数量太大从而导致对象内存开销加大——什么样的数量才算大？这需要我们仔细的根据具体应用情况进行评估，而不能凭空臆断。
