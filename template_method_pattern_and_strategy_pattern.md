# 20200902
## Template Method Pattern

```java
public abstract class AbstractEveryday {
    /**
     * 1. 朝
     * 2. 昼
     * 3. 夜
     * 4. 寝る
     */

    public final void start() {
        startMessage();
        morning();
        separate();
        daytime();
        separate();
        night();
        separate();
        sleep();
    }

    private void startMessage() {
        System.out.println("[ S T A R T !! ]");
    }

    protected abstract void morning();

    protected abstract void daytime();

    protected abstract void night();

    private void sleep() {
        System.out.println("(つ∀-)ｵﾔｽﾐｰ..... [ E N D !! ]");
    }

    private void separate() {
        System.out.println("↓");
    }
}
```

```java
public class BankerEveryday extends AbstractEveryday {

    @Override
    protected void morning() {
        System.out.println("おはようございます！");
    }

    @Override
    protected void daytime() {
        System.out.println("電話セールス！");

    }

    @Override
    protected void night() {
        System.out.println("飲み会！");
    }
}
```

```java
public class StudentEveryday extends AbstractEveryday {

    @Override
    protected void morning() {
        System.out.println("(。-ω-)zzz");
    }

    @Override
    protected void daytime() {
        System.out.println("(。-ω-)zzz");
    }

    @Override
    protected void night() {
        System.out.println("ゲーム！");
    }
}
```

## Template Method Pattern(interface)

```java
public interface Everyday2 {
    /**
     * 1. 朝
     * 2. 昼
     * 3. 夜
     * 4. 寝る
     */

    default void start() {
        System.out.println("[ S T A R T !! ]");
        morning();
        System.out.println("↓");
        daytime();
        System.out.println("↓");
        night();
        System.out.println("↓");
        System.out.println("(つ∀-)ｵﾔｽﾐｰ..... [ E N D !! ]");
    }

    void morning();

    void daytime();

    void night();
}
```

```java
public class BankerEveryday2 implements Everyday2 {
    @Override
    public void morning() {
        System.out.println("おはようございます！");
    }

    @Override
    public void daytime() {
        System.out.println("電話セールス！");
    }

    @Override
    public void night() {
        System.out.println("飲み会！");
    }
}
```

```java
public class StudentEveryday2 implements Everyday2 {
    @Override
    public void morning() {
        System.out.println("(。-ω-)zzz");
    }

    @Override
    public void daytime() {
        System.out.println("(。-ω-)zzz");
    }

    @Override
    public void night() {
        System.out.println("ゲーム！");

    }
}
```

## Template Method Pattern(functional interface) (Lambda)

```java
@FunctionalInterface
public interface Everyday3 {
    /**
     * 1. 日中
     * 2. 寝る
     */

    default void start(String daytimeActivity) {
        System.out.println("[ S T A R T !! ]");
        daytime(daytimeActivity);
        System.out.println("(つ∀-)ｵﾔｽﾐｰ..... [ E N D !! ]");
    }

    void daytime(String daytimeActivity);
}
```

## Strategy Pattern

```java
public class EverydayContext {
    EverydayStrategy everydayStrategy;

    public EverydayContext(EverydayStrategy everydayStrategy) {
        this.everydayStrategy = everydayStrategy;
    }

    public void start() {
        everydayStrategy.start();
    }
}
```

```java
public interface EverydayStrategy {
    /**
     * 1. 朝
     * 2. 昼
     * 3. 夜
     * 4. 寝る
     */

    default void start() {
        System.out.println("[ S T A R T !! ]");
        morning();
        System.out.println("↓");
        daytime();
        System.out.println("↓");
        night();
        System.out.println("↓");
        System.out.println("(つ∀-)ｵﾔｽﾐｰ..... [ E N D !! ]");
    }

    void morning();

    void daytime();

    void night();
}
```

```java
public class BankerEverydayStrategy implements EverydayStrategy {
    @Override
    public void morning() {
        System.out.println("おはようございます！");
    }

    @Override
    public void daytime() {
        System.out.println("電話セールス！");
    }

    @Override
    public void night() {
        System.out.println("飲み会！");
    }
}
```

```java
public class StudentEverydayStrategy implements EverydayStrategy {
    @Override
    public void morning() {
        System.out.println("(。-ω-)zzz");
    }

    @Override
    public void daytime() {
        System.out.println("(。-ω-)zzz");
    }

    @Override
    public void night() {
        System.out.println("ゲーム！");
    }
}
```
