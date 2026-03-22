FROM python:3.11-slim

WORKDIR /app

RUN useradd -r -s /bin/false appuser

COPY --chown=appuser:appuser app.py .

EXPOSE 8080

USER appuser

HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
  CMD python3 -c "import urllib.request; urllib.request.urlopen('http://localhost:8080/')" || exit 1

CMD ["python", "app.py"]
