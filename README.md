## Create Custom Pagination Design in Laravel 7

First of all we need is execute this artisan command:
```php
php artisan vendor:publish --tag=laravel-pagination
```

And now just replace the html content and setup the pagination view of : resources/views/vendor/pagination/default.blade.php with this code:

```php
@if ($paginator->hasPages())
    <nav class="pagination is-centered">
        @if ($paginator->onFirstPage())
            <a class="pagination-previous" disabled>Previous</a>
        @else
            <a href="{{ $paginator->previousPageUrl() }}" rel="prev" class="pagination-previous">Previous</a>
        @endif

        @if ($paginator->hasMorePages())
            <a class="pagination-next" href="{{ $paginator->nextPageUrl() }}" rel="next">Next</a>
        @else
            <a class="pagination-next" disabled>Next page</a>
        @endif

        <ul class="pagination-list">
            {{-- Pagination Elements --}}
            @foreach ($elements as $element)
                {{-- "Three Dots" Separator --}}
                @if (is_string($element))
                    <li><span class="pagination-ellipsis"><span>{{ $element }}</span></span></li>
                @endif

                {{-- Array Of Links --}}
                @if (is_array($element))
                    @foreach ($element as $page => $url)
                        @if ($page == $paginator->currentPage())
                            <li><a class="pagination-link is-current">{{ $page }}</a></li>
                        @else
                            <li><a href="{{ $url }}" class="pagination-link">{{ $page }}</a></li>
                        @endif
                    @endforeach
                @endif
            @endforeach
        </ul>
    </nav>
@endif
```

Now call pagination like this:
```php
{{ $data->links('vendor.pagination.default') }}
```


### Connect With Me
Telegram - https://t.me/techcvr <br>
Discord - https://discord.gg/bcH8nGU <br>
YouTube - https://www.youtube.com/techcvr <br>
Instagram - https://www.instagram.com/vishalgaire/
