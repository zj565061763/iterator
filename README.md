# About
支持正序遍历和倒序遍历的遍历器

```java
public class MainActivity extends AppCompatActivity
{
    public static final String TAG = MainActivity.class.getSimpleName();

    private List<String> mList = new ArrayList<>();

    @Override
    protected void onCreate(Bundle savedInstanceState)
    {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        for (int i = 0; i < 10; i++)
        {
            mList.add(String.valueOf(i));
        }

        doNext();
        doPrevious();
    }

    /**
     * 正序遍历
     */
    private void doNext()
    {
        FIterator<String> it = new FListIterator<>(mList);
        it.prepareNext(); //准备正序遍历
        while (it.hasNext())
        {
            String item = it.next();
            Log.i(TAG, item);

            if (it.index() % 2 == 0)
            {
                it.remove(); //移除index被2整除的数据
            }
        }
    }

    /**
     * 倒序遍历
     */
    private void doPrevious()
    {
        FIterator<String> it = new FListIterator<>(mList);
        it.preparePrevious(); //准备倒序遍历
        while (it.hasPrevious())
        {
            String item = it.previous();
            Log.e(TAG, item);
        }
    }
}
```